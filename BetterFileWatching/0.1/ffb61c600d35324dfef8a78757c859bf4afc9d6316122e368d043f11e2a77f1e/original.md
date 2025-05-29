```julia
watch_file(f::Function, filename::AbstractString)
```

Watch a file recursively for any changes. A [`FileEvent`](@ref) is passed to the callback function `f` when a change occurs.

Use the single-argument `watch_file(filename::AbstractString)` to create a **blocking call** until the file changes (like the FileWatching standard library).

# Example

```julia
watch_file("file.txt") do event
    @info "Something changed!" event
end
```

You can watch a file asynchronously, and interrupt the task later:

```julia
watch_task = @async watch_file("file.txt") do event
    @info "Something changed!" event
end

sleep(5)

# stop watching the file
schedule(watch_task, InterruptException(); error=true) 
```

# Differences with the FileWatching stdlib

  * BetterFileWatching.jl is based on [Deno.watchFs](https://doc.deno.land/builtin/stable#Deno.watchFs), made available through the [Deno_jll](https://github.com/JuliaBinaryWrappers/Deno_jll.jl) package.
