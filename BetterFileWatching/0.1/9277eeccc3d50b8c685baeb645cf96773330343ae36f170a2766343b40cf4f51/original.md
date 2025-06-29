```julia
watch_folder(f::Function, dir=".")
```

Watch a folder recursively for any changes. Includes changes to file contents. A [`FileEvent`](@ref) is passed to the callback function `f`.

Use the single-argument `watch_folder(dir::AbstractString=".")` to create a **blocking call** until the folder changes (like the FileWatching standard library).

# Example

```julia
watch_folder(".") do event
    @info "Something changed!" event
end
```

You can watch a folder asynchronously, and interrupt the task later:

```julia
watch_task = @async watch_folder(".") do event
    @info "Something changed!" event
end

sleep(5)

# stop watching the folder
schedule(watch_task, InterruptException(); error=true) 
```

# Differences with the FileWatching stdlib

  * `BetterFileWatching.watch_folder` works *recursively*, i.e. subfolders are also watched.
  * `BetterFileWatching.watch_folder` also watching file *contents* for changes.
  * BetterFileWatching.jl is based on [Deno.watchFs](https://doc.deno.land/builtin/stable#Deno.watchFs), made available through the [Deno_jll](https://github.com/JuliaBinaryWrappers/Deno_jll.jl) package.
