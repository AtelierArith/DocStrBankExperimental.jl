```
runserver(pipe_in=stdin, pipe_out=stdout[, env_path])
```

Run a `LanguageServerInstance` reading from `pipe_in` and writing to `pipe_out`.

The same options can be passed to `runserver` as to [`LanguageServerInstance`](@ref). If `env_path` is not specified, attempt to pick an environment by considering in order of priority:

1. [`ARGS`[1]](@ref): the first command-line argument passed to the invocation of `julia`.
2. The Julia project containing [`pwd()`](@ref).
3. The default Julia environment withing `.julia/environments/v#.#`.

# Examples

The following invocation of Julia would set `env_path` to `/home/example/repos/Example.jl`:

```sh
julia --project=/path/to/LanguageServer.jl \
  -e "using LanguageServer; runserver()" \
  /home/example/repos/Example.jl
```

If there was a `Project.toml` or `JuliaProject.toml` in `/home/example/repos/Example.jl/`, the following invocation would set `env_path` to `/home/example/repos/Example.jl/`; otherwise it would be set to `.julia/environments/v#.#` where `v#.#` is the major/minor version of Julia being invoked.

```sh
julia --project=/path/to/LanguageServer.jl \
  -e "using LanguageServer; runserver()"
```
