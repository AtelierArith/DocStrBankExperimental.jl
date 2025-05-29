wrapit(;`args`)

Launch the [wrapit](https://www.github.com/grasph/wrapit) command. The command options are passed as function arguments in the form of:

  * <option name>=<option value> for options that takes an argument. E.g., `resource_dir=/usr/lib/...` to pass `--resource-dir=/usr/lib...` option.
  * <option name>=true for options with no argument. E.g., `force=true` to pass the `--force` option.

Underscores are used in the argument name in place of dashs used in the option name.

Call `wrapit(help=true)` to get the list of options.

If `returncode = true` is passed as argument, the function returns the exit code of the `wrapit` command (0 in case of success) and `nothing` otherwise.
