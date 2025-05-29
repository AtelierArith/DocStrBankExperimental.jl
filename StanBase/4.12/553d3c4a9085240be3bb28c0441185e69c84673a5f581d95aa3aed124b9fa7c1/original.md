The directory which contains the cmdstan executables such as `bin/stanc` and `bin/stansummary`. 

# Extended help

Inferred from the environment variable `CMDSTAN` or `ENV["CMDSTAN"]` when available.

If these are not available, use `set_cmdstan_home!` to set the value of CMDSTAN_HOME.

Example: `set_cmdstan_home!(homedir() * "/Projects/Stan/cmdstan/")`

Executing `versioninfo()` will display the value of `CMDSTAN` if defined.
