# Package.json

Original version of this document copied from [yarnpkg](https://yarnpkg.com/lang/en/docs/package-json/).

See also [npm documentation](https://docs.npmjs.com/files/package.json), [package-json-validator](http://package-json-validator.com/).

<!-- toc -->

- [Essentials](#essentials)
  * [`name`](#name)
  * [`version`](#version)
- [Info](#info)
  * [`description`](#description)
  * [`keywords`](#keywords)
  * [`license`](#license)
- [Links](#links)
  * [`homepage`](#homepage)
  * [`bugs`](#bugs)
  * [`repository`](#repository)
- [Maintainers](#maintainers)
  * [`author`](#author)
  * [`contributors`](#contributors)
- [Files](#files)
  * [`files`](#files)
  * [`main`](#main)
  * [`bin`](#bin)
  * [`man`](#man)
  * [`directories`](#directories)
- [Tasks](#tasks)
  * [`scripts`](#scripts)
  * [`config`](#config)
- [Dependencies](#dependencies)
  * [`dependencies`](#dependencies)
  * [`devDependencies`](#devdependencies)
  * [`peerDependencies`](#peerdependencies)
  * [`optionalDependencies`](#optionaldependencies)
  * [`bundledDependencies`](#bundleddependencies)
- [System](#system)
  * [`engines`](#engines)
  * [`os`](#os)
  * [`cpu`](#cpu)
- [Publishing](#publishing)
  * [`private`](#private)
  * [`publishConfig`](#publishconfig)
- [Yarn](#yarn)
  * [`flat`](#flat)
  * [`resolutions`](#resolutions)
- [TypeScript](#typescript)
  * [`types`](#types)
- [Package bundlers](#package-bundlers)
  * [`module`](#module)
  * [`browser`](#browser)
  * [`module-browser`](#module-browser)
  * [`jsnext:main`](#jsnextmain)
- [browserslist](#browserslist)
  * [`browserslist`](#browserslist)
- [babel](#babel)
  * [`babel`](#babel)
- [eslint](#eslint)
  * [`eslintConfig`](#eslintconfig)
- [Other](#other)
  * [`preferGlobal`](#preferglobal)
  * [`style`](#style)
- [nodejitsu](#nodejitsu)
  * [`subdomain`](#subdomain)
  * [`domains`](#domains)
  * [`env`](#env)
  * [`analyze`](#analyze)

<!-- tocstop -->

## Essentials

The two most important fields in your `package.json` are `name` and `version`,
without them your package won't be able to install. The `name` and `version`
fields are used together to create a unique id.

### `name`

```json
{
  "name": "my-awesome-package"
}
```

This is the name of your package. It gets used in URLs, as an argument on the
command line, and as the directory name inside `node_modules`.

```sh
yarn add [name]
```

```
node_modules/[name]
```

```
https://registry.npmjs.org/[name]/-/[name]-[version].tgz
```

**Rules**

- Must be less than or equal to 214 characters (including the `@scope/` for
  scoped packages).
- Must not start with a dot (`.`) or an underscore (`_`).
- Must not have an uppercase letter in the name.
- Must use only URL-safe characters.

**Tips**

- Don't use the same name as a core Node.js module
- Don't put `js` or `node` in the name.
- Keep names short and descriptive. You want people to understand what it is
  from the name, but it will also be used in `require()` calls.
- Make sure that there isn't something in the
  [registry](https://www.npmjs.com/) with the same name.

### `version`

```json
{
  "version": "1.0.0"
}
```
The current version of your package.

## Info

### `description`

```json
{
  "description": "My short description of my awesome package"
}
```

The description is just a string that helps people understand the purpose of the package. It can be used when searching for packages in a package manager as well.

### `keywords`

```json
{
  "keywords": ["short", "relevant", "keywords", "for", "searching"]
}
```

Keywords are an array of strings that are useful when searching for packages in a package manager.

### `license`

```json
{
  "license": "MIT",
  "license": "(MIT or GPL-3.0)",
  "license": "SEE LICENSE IN LICENSE_FILENAME.txt",
  "license": "UNLICENSED"
}
```

All packages should specify a license so that users know how they are permitted
to use it and any restrictions that you are placing on it.

You are encouraged to use an Open Source
([OSI-approved](https://opensource.org/licenses/alphabetical)) license unless
you have a specific reason not to. If you built your package as part of your
job it's likely best to check with your company before deciding on a license.

**Must be one of the following:**

- A valid [SPDX license identifier](https://spdx.org/licenses/) if you are
  using a standard license.
- A valid
  [SPDX license expression syntax 2.0 expression](https://www.npmjs.com/package/spdx)
  if you are using multiple standard licenses.
- A `SEE LICENSE IN <filename>` string that points to a `<filename>` in the top
  level of your package if you are using a non-standard license.
- A `UNLICENSED` string if you do not want to grant others the right to use a
  private or unpublished package under any terms.

## Links

Various links to documentation, places to file issues and where your package code actually lives.

### `homepage`

```json
{
  "homepage": "https://your-package.org"
}
```

The homepage is the URL to the landing page or documentation for your package.

Also used by [Create React App](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md#building-for-relative-paths)

### `bugs`

```json
{
  "bugs": "https://github.com/user/repo/issues"
}
```

The URL to your project's issue tracker. This can also be something like an email address as well. It provides users a way to find out where to send issues with your package.

### `repository`

```json
{
  "repository": { "type": "git", "url": "https://github.com/user/repo.git" },
  "repository": "github:user/repo",
  "repository": "gitlab:user/repo",
  "repository": "bitbucket:user/repo",
  "repository": "gist:a1b2c3d4e5f"
}
```

The repository is the location where the actual code for your package lives.

## Maintainers

The maintainers of your project.

### `author`

```json
{
  "author": { "name": "Your Name", "email": "you@example.com", "url": "http://your-website.com" },
  "author": "Your Name <you@example.com> (http://your-website.com)"
}
```

Package author information. An author is one person.

### `contributors`

```json
{
  "contributors": [
    { "name": "Your Friend", "email": "friend@example.com", "url": "http://friends-website.com" }
    { "name": "Other Friend", "email": "other@example.com", "url": "http://other-website.com" }
  ],
  "contributors": [
    "Your Friend <friend@example.com> (http://friends-website.com)",
    "Other Friend <other@example.com> (http://other-website.com)"
  ]
}
```

Those that have contributed to your package. Contributors are an array of people.

## Files

You can specify files that will be included in your project, along with the main entry point for your project.

### `files`

```json
{
  "files": [
    "filename.js",
    "directory/",
    "glob/*.{js,json}"
  ]
}
```

These are files that are included in your project. You can specify single files, whole directories or use wildcards to include files that meet a certain criteria.

### `main`

```json
{
  "main": "filename.js"
}
```

This is the primary entry point for the functionality for your project.

### `bin`

```json
{
  "bin": "bin.js",
  "bin": {
    "command-name": "bin/command-name.js",
    "other-command": "bin/other-command"
  }
}
```

Executable files included with your project that will be installed.

### `man`

```json
{
  "man": "./man/doc.1",
  "man": ["./man/doc.1", "./man/doc.2"]
}
```

If you have man pages associated with your project, add them here.

### `directories`

```json
{
  "directories": {
    "lib": "path/to/lib/",
    "bin": "path/to/bin/",
    "man": "path/to/man/",
    "doc": "path/to/doc/",
    "example": "path/to/example/"
  }
}
```

When installing your package, you can specify exact locations to put binary files, man pages, documentation, examples, etc.

## Tasks

Your package can include runnable scripts or other configuration.

### `scripts`

```json
{
  "scripts": {
    "build-project": "node build-project.js"
  }
}
```

Scripts are a great way of automating tasks related to your package, such as simple build processes or development tools. Using the `"scripts"` field, you can define various scripts to be run as `yarn run <script>`. For example, the `build-project` script above can be invoked with `yarn run build-project` and will run `node build-project.js`.

Certain script names are special. If defined, the `preinstall` script is called by yarn before your package is installed. For compatibility reasons, scripts called `install`, `postinstall`, and `prepublish` will all be called after your package has finished installing.

The `start` script value defaults to `node server.js`.

> `"scripts": {"start": "node server.js"}`. If there is a server.js file in the root of your package, then npm will default the start command to node server.js.
>
> `"scripts":{"preinstall": "node-gyp rebuild"}`. If there is a binding.gyp file in the root of your package, npm will default the preinstall command to compile using node-gyp.
>
> -- [npm docs](https://docs.npmjs.com/files/package.json#default-values)

### `config`

```json
{
  "config": {
    "port": "8080"
  }
}
```

Configuration options or parameters used in your scripts.

## Dependencies

Your package will very likely depend on other packages. You can specify those dependencies in your `package.json` file.

### `dependencies`

```json
{
  "dependencies": {
    "package-1": "^3.1.4"
  }
}
```

These are dependencies that are required in both development and production for your package.

> You can specify an exact version, a minimum version (e.g., `>=`) or a range of versions (e.g. `>= ... <`).

### `devDependencies`

```json
{
  "devDependencies": {
    "package-2": "^0.4.2"
  }
}
```

These are packages that are only required when developing your package but will not be installed in production.

### `peerDependencies`

```json
{
  "peerDependencies": {
    "package-3": "^2.7.18"
  }
}
```

Peer dependencies allow you to state compatibility of your package with versions of other packages.

### `optionalDependencies`

```json
{
  "optionalDependencies": {
    "package-5": "^1.6.1"
  }
}
```

Optional dependencies can be used with your package, but are not required. If the optional package is not found, installation still continues.

### `bundledDependencies`

```json
{
  "bundledDependencies": [
    "package-4"
  ]
}
```

Bundled dependencies are an array of package names that will be bundled together when publishing your package.

## System

You can provide system-level information associated with your package, such as operating system compatibility, etc.

### `engines`

```json
{
  "engines": {
    "node": ">=4.4.7 <7.0.0",
    "zlib": "^1.2.8",
    "yarn": "^0.14.0"
  }
}
```

The engines specify versions of clients that must be used with your package. This checks against `process.versions` as well as the current version of yarn.

### `os`

```json
{
  "os": ["darwin", "linux"],
  "os": ["!win32"]
}
```

This specifies operating system compatibility for your package. It checks against `process.platform`.

### `cpu`

```json
{
  "cpu": ["x64", "ia32"],
  "cpu": ["!arm", "!mips"]
}
```

Use this to specify your package will only run on certain CPU architectures. This checks against `process.arch`.

## Publishing

### `private`

```json
{
  "private": true
}
```

If you do not want your package published in a package manager, set this to `true`.

### `publishConfig`

```json
{
  "publishConfig": {
    ...
  }
}
```

These configuration values will be used when publishing your package. You can tag your package, for example.

## Yarn


### `flat`

```json
{
  "flat": true
}
```

If your package only allows one version of a given dependency, and you'd like to enforce the same behavior as [`yarn install --flat`]({{url_base}}/docs/cli/install#toc-yarn-install-flat) on the command line, set this to `true`.

Note that if your `package.json` contains `"flat": true` and other packages depend on yours (e.g. you are building a library rather than an application), those other packages will also need `"flat": true` in their `package.json` or be installed with `yarn install --flat` on the command line.

### `resolutions`


```json
{
  "resolutions": {
    "transitive-package-1": "0.0.29",
    "transitive-package-2": "file:./local-forks/transitive-package-2",
    "dependencies-package-1/transitive-package-3": "^2.1.1"
  }
}
```

Allows you to override a version of a particular nested dependency. See [the Selective Versions Resolutions RFC](https://github.com/yarnpkg/rfcs/blob/master/implemented/0000-selective-versions-resolutions.md) for the full spec.

Note that installing dependencies via [`yarn install --flat`] will automatically add a `resolutions` block to your `package.json` file.

## TypeScript

### `types`

If your package has a main `.js` file, you will need to indicate the main declaration file in your `package.json` file as well. Set the `types` property to point to your bundled declaration file. For example:

```json
{
    "main": "./lib/main.js",
    "types": "./lib/main.d.ts"
}
```

Note that the `typings` field is synonymous with `types`, and could be used as well.

Also note that if your main declaration file is named `index.d.ts` and lives at the root of the package (next to `index.js`) you do not need to mark the `types` property, though it is advisable to do so.

Source: [TypeScript documentation](https://www.typescriptlang.org/docs/handbook/declaration-files/publishing.html)

Note: in Flow they use [different approach](https://medium.com/netscape/shipping-flowtype-definitions-in-npm-packages-c987917efb65)

## Package bundlers

### `module`

`pkg.module` will point to a module that has ES2015 module syntax but otherwise only syntax features that the target environments support. Full description is [here](https://github.com/rollup/rollup/wiki/pkg.module).

Supported by: rollup, webpack

### `browser`

The `browser` field is provided by a module author as a hint to javascript bundlers or component tools when packaging modules for client side use. Proposal is [here](https://github.com/defunctzombie/package-browser-field-spec).

Supported by: webpack

### `module-browser`

See this [issue](https://github.com/webpack/webpack/issues/4674)

### `jsnext:main`

**DEPRECATED**

`jsnext:main` has been superseded by `pkg.module`, which indicates the location of a file with import/export declarations.

Original proposal is [here](https://github.com/jsforum/jsforum/issues/5).

## browserslist

### `browserslist`

Library to share target browsers between different front-end tools.
It is used in:

* [Autoprefixer]
* [babel-preset-env]
  (external config in `package.json` or `browserslist` files supported in 2.0)
* [postcss-preset-env]
* [eslint-plugin-compat]
* [stylelint-no-unsupported-browser-features]
* [postcss-normalize]

All tools that rely on Browserslist will find its config automatically,
when you add the following to `package.json`:

```json
{
  "browserslist": [
    "> 1%",
    "last 2 versions"
  ]
}
```

[stylelint-no-unsupported-browser-features]: https://github.com/ismay/stylelint-no-unsupported-browser-features
[eslint-plugin-compat]:                      https://github.com/amilajack/eslint-plugin-compat
[postcss-preset-env]: https://github.com/jonathantneal/postcss-preset-env
[babel-preset-env]:                          https://github.com/babel/babel/tree/master/packages/babel-preset-env
[postcss-normalize]:                         https://github.com/jonathantneal/postcss-normalize
[Autoprefixer]:                              https://github.com/postcss/autoprefixer

## babel

### `babel`

See this [issue](https://github.com/babel/babel-preset-env/issues/149).

## eslint

### `eslintConfig`

## Other

### `preferGlobal`

**DEPRECATED**

This option used to trigger an npm warning, but it will no longer warn. It is purely there for informational purposes. It is now recommended that you install any binaries as local devDependencies wherever possible.

### `style`

The `style` attribute in `package.json` is useful for importing CSS packages. Proposal is [here](https://jaketrent.com/post/package-json-style-attribute/).

## nodejitsu

Source: [nodejitsu documentation](https://www.nodejitsu.com/documentation/appendix/package-json/#nodejitsu-specific-package-json-properties)

### `subdomain`

Specify the subdomain for your hosted app's Nodejitsu URL (for example, subdomain.nodejitsu.com.

### `domains`

A list of custom domains for your hosted app.

### `env`

Specify environment variables for your app (for example, `NODE_ENV="production"` is set by default).

### `analyze`

Set this to "false" to force jitsu to not analyze for the app's dependencies.

