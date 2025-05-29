The directory which contains the cmdstan executables such as `bin/stanc` and `bin/stansummary`. Inferred from the environment variable `JULIA_CMDSTAN_HOME` or `ENV["JULIA_CMDSTAN_HOME"]` when available.

If these are not available, use `set_cmdstan_home!` to set the value of CMDSTAN_HOME.

Example: `set_cmdstan_home!(homedir() * "/Projects/Stan/cmdstan/")`

Executing `versioninfo()` will display the value of `JULIA_CMDSTAN_HOME` if defined.
