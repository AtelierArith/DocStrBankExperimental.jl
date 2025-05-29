```
@always_everywhere(expr)
```

Runs `expr` on all current Julia processes, but also all future Julia processes after an [`ensure_procinit()`](@ref)) when managed using a [`FlexWorkerPool`](@ref).

Similar to `Distributed.everywhere`, but also stores `expr` so that `ensure_procinit` can execute it on future worker processes.

Example:

```julia
@always_everywhere begin
    using SomePackage
    using SomeOtherPackage
    
    some_global_variable = 42
end
```

See also [`ParallelProcessingTools.add_procinit_code`](@ref) and [`ParallelProcessingTools.ensure_procinit`](@ref).
