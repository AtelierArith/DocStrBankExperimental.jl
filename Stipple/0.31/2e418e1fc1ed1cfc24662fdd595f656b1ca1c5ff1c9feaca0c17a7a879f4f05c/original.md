```
@stipple_precompile(setup, workload)
```

A macro that facilitates the precompilation process for Stipple-related code.

# Arguments

  * `setup`: An optional setup configuration that is required for the precompilation.
  * `workload`: The workload or tasks that need to be precompiled.

The macro defines three local routines: `precompile_get`, `precompile_post`, and `precompile_request`. These routines can be used to send requests to the local server that is started during the precompilation process.

The envrionment variable ENV["STIPPLE*PRECOMPILE*REQUESTS"] can be set to "false" to disable the precompilation of HTTP.requests. The default value is "true".

# Example (see also end of Stipple.jl)

```
module MyApp
using Stipple, Stipple.ReactiveTools

@app PrecompileApp begin
    @in demo_i = 1
    @out demo_s = "Hi"

    @onchange demo_i begin
    println(demo_i)
    end
end

ui() = [cell("hello"), row("world"), htmldiv("Hello World")]

function __init__()
    @page("/", ui)
end

@stipple_precompile begin
    # the @page macro cannot be called here, as it reilies on writing some cache files to disk
    # hence, we use a manual route definition for precompilation

    route("/") do
        model = @init PrecompileApp
        page(model, ui) |> html
    end

    precompile_get("/")
end

end
```
