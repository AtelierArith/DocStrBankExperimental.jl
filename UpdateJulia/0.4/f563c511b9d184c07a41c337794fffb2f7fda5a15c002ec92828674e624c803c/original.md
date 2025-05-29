```
update_julia(version::AbstractString="")
```

Install the latest version of Julia from https://julialang.org

If `version` is provided, installs the latest version that starts with `version`. If `version == "nightly"`, then installs the bleeding-edge nightly version.

# Keyword Arguments

Behavior flags

  * `dry_run = false` skip the actual download and installation
  * `verbose = dry_run` print the final value of all arguments
  * `migrate_packages = <upgrading to a later version of Julia without an existing global environment>` whether to migrate packages in the default global environment. May be `true`, `false`, or `:force`. Only `:force` will replace an existing Project.toml

Destination

  * `aliases = ["julia", "julia-$(v.major).$(v.minor)", "julia-$v"]` which aliases to attempt to create for the installed version of Julia. Regardless, will not replace stable versions with less stable versions or newer versions with older versions of the same stability.
  * `systemwide = false` install for all users, `false` only installs for current user.
  * `install_location = systemwide ? "/opt" : "/home/terasaki/.julia/juliaup"` directory to put installed binaries
  * `bin = systemwide ? "/usr/local/bin" : "/home/terasaki/.local/bin"` directory to store links to the binaries

Source

  * `os_str = "linux"` string representation of the operating system: "linux", "mac", "winnt", or "freebsd".
  * `arch = "x86_64"` string representation of the CPU architecture: "x86_64", "i686", "aarch64", "armv7l", or "powerpc64le".
  * `v = ...` the `VersionNumber` to install
  * `url = ...` URL to download that version from, if you explicitly set `url`, also explicitly set `v` lest they differ
