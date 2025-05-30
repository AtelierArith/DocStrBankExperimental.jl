```
@local name = value

@local name::T = value
```

Can be used inside a `@tasks for ... end` block to specify [task-local values](@ref TLS) (TLV) via explicitly typed assignments. These values will be allocated once per task (rather than once per iteration) and can be re-used between different task-local iterations.

There can only be a single `@local` block in a `@tasks for ... end` block. To specify multiple TLVs, use `@local begin ... end`. Compared to regular assignments, there are some limitations though, e.g. TLVs can't reference each other.

## Examples

```julia
using OhMyThreads: @tasks
using OhMyThreads.Tools: taskid

@tasks for i in 1:10
    @set begin
        scheduler=:dynamic
        ntasks=2
    end
    @local x = zeros(3) # TLV

    x .+= 1
    println(taskid(), " -> ", x)
end
```

```julia
@tasks for i in 1:10
    @local begin
        x = rand(Int, 3)
        M = rand(3, 3)
    end
    # ...
end
```

Task local variables created by `@local` are by default constrained to their inferred type, but if you need to, you can specify a different type during declaration:

```julia
@tasks for i in 1:10
    @local x::Vector{Float64} = some_hard_to_infer_setup_function()
    # ...
end
```

The right hand side of the assignment is hoisted outside of the loop body and captured as a closure used to initialize the task local value. This means that the scope of the closure is *not* the scope of the loop (even though it looks like it) but rather the scope *surrounding* the loop body. (`@macroexpand` is a useful tool to inspect the generated code of the `@tasks` block.)
