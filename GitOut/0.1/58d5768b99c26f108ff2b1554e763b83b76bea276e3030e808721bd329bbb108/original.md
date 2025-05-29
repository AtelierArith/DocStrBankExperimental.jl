```julia
git(
;
    use_system,
    adjust_PATH,
    adjust_LIBPATH,
    env,
    dir
) -> Cmd

```

Returns a `git` command as a `Cmd` object.

## Keyword Arguments

  * `use_system`: whether or not to use system git.  See [`use_system_git!`](@ref).  Defaults to `false`   if this was not called.
  * `adjust_PATH=false`: whether or not to adjust the `PATH` variable when using `Git_jll`.
  * `adjust_LIBPATH=true`: whether or not to adjust the `LIBPATH` variable when using `Git_jll`.
  * `env=ENV`: A key-value collection specifying the environemnt for the command, see `Base.ENV`.
  * `dir=""`: Directory for which to run the `git` command.  This uses the `-C` option for `git`.  If empty,   the `-C` argument will not be passed.
