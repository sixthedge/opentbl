# OpenTBL: The new standard in Online Team-Based Learning
OpenTBL provides the best open source software to bring the effective and engaging TBL pedagogy to your online course - all while saving you time and increasing student satisfaction.

**Teach more. Manage less.**
 * Electronically create and disseminate individual and team Readiness Assurance Tests (iRAT/tRAT), Peer Evaluations, and application exercises. 
 * No more paper shuffling, miskeyed forms, or manual scoring.
 * Access modules anytime, anywhere. Support for desktops, tablets, and mobile devices.
 * Pedagogically sound templates that streamline the building process for experienced faculty and jumpstart the process for new faculty.
 * Create once, use forever. Copy all your modules to a new course or term at the click of a button.
 
## Code
### Repository
[This page](https://github.com/sixthedge/opentbl/) is the issue-only repository for the OpenTBL project.  The actual source code is located in the [Cellar](https://github.com/sixthedge/cellar/) and is installed through the `totem-app` CLI commands.

## Setup
This is a quick setup guide for getting a working development environment up for Thinkspace and Totem based applications. Development is supported on Debian 9 ([Strech](https://wiki.debian.org/DebianStretch)) based systems such as [Ubuntu 16.04](http://releases.ubuntu.com/16.04/) or [Mint 18](https://www.linuxmint.com/release.php?id=27). See our complete [Setup Guide](http://totem-docs.herokuapp.com/1.0.1/setup/environment) for a more in-depth overview.

### Prerequisites
These are the required tools that you will need to have in your environment, links are provided with instructions on how to install them below.

- [Git](http://totem-docs.herokuapp.com/1.0.1/setup/environment#install-git) **2.7.4**
- [Postgres](http://totem-docs.herokuapp.com/1.0.1/setup/environment#install-postgresql) **v9.5.5**
- [Rvm](http://totem-docs.herokuapp.com/1.0.1/setup/environment#install-rvm) **1.27.0** 
- [Ruby](http://totem-docs.herokuapp.com/1.0.1/setup/environment#install-ruby) **2.3.1**
- [Rails ](http://totem-docs.herokuapp.com/1.0.1/setup/environment#install-rails-5) **5.0.0.1**
- [NVM ](http://totem-docs.herokuapp.com/1.0.1/setup/environment#install-nvm) **0.32.1**
- [node](http://totem-docs.herokuapp.com/1.0.1/setup/environment#install-node) **6.9.1**
- ember **2.8**
- ember-data **2.8.1**
- [ember-cli](http://totem-docs.herokuapp.com/1.0.1/setup/environment#install-ember-cli-bower) **2.9.1**
- [redis-server](http://totem-docs.herokuapp.com/1.0.1/setup/environment#install-redis) **3.0.6**

_Versions are at the minimum requirements._

### Installation
- Create a directory that will hold the applications and code. This directory can be named or placed wherever in your file system, but we recommend at the base of your user's directory. _(e.g. `~/Projects/`)_
- Inside your new folder clone the [Cellar](https://github.com/sixthedge/cellar) repo and create two new directories `apps-rails` and `apps-ember`. These are **required** for the build process.
- From the base of the `cellar` repo, run [totem-ember-cli](https://github.com/sixthedge/cellar/blob/master/src/totem/api/totem-cli/lib/totem/cli/totem_ember.rb) to build the client app.
```
  $ ./src/totem/api/totem-cli/bin/totem-ember-cli ../apps-ember/orchid -o ./thinkspace/packages/otbl/client/run.yml --new -f -n
```
- From the root of the `cellar` repo, run [totem-app](https://github.com/sixthedge/cellar/blob/master/src/totem/api/totem-cli/lib/totem/cli/totem_app.rb) to build the API app.
```
  $ ./src/totem/api/totem-cli/bin/totem-ember-cli ../apps-rails/orchid -o ./thinkspace/packages/otbl/client/run.yml --new -f
```
- From the newly generated `apps-rails/orchid` directory run 
  - `$ bundle install` 
  - `$ db:drop db:create totem:db:reset[ra] CONFIG=all AI=true`

### Running the Servers
After completing the steps above you should now have two generated applications inside their respective folders.

```
-| ~/Projects
  -| apps-ember
    -| orchid #=> [Client] Run `ember server`
  -| apps-rails
    - | orchid #=> [API] Run `rails s`
  -| cellar
```
