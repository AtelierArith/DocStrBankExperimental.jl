```
LanguageServerInstance(pipe_in, pipe_out, env="", depot="", err_handler=nothing, symserver_store_path=nothing)
```

Construct an instance of the language server.

Once the instance is `run`, it will read JSON-RPC from `pipe_out` and write JSON-RPC from `pipe_in` according to the [language server specification](https://microsoft.github.io/language-server-protocol/specifications/specification-3-14/). For normal usage, the language server can be instantiated with `LanguageServerInstance(stdin, stdout, false, "/path/to/environment")`.

# Arguments

  * `pipe_in::IO`: Pipe to read JSON-RPC from.
  * `pipe_out::IO`: Pipe to write JSON-RPC to.
  * `env::String`: Path to the [environment](https://docs.julialang.org/en/v1.2/manual/code-loading/#Environments-1) for which the language server is running. An empty string uses julia's default environment.
  * `depot::String`: Sets the [`JULIA_DEPOT_PATH`](https://docs.julialang.org/en/v1.2/manual/environment-variables/#JULIA_DEPOT_PATH-1) where the language server looks for packages required in `env`.
  * `err_handler::Union{Nothing,Function}`: If not `nothing`, catch all errors and pass them to an error handler function with signature `err_handler(err, bt)`. Mostly used for the VS Code crash reporting implementation.
  * `symserver_store_path::Union{Nothing,String}`: if `nothing` is passed, the symbol server cash is stored in a folder in the package. If an absolute path is passed, the symbol server will store the cache files in that path. The path must exist on disc before this is called.
