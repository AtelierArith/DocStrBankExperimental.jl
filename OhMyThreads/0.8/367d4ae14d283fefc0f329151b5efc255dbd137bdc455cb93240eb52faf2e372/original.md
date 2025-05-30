```
@tasks for ... end
```

A macro to parallelize a `for` loop by spawning a set of tasks that can be run in parallel. The policy of how many tasks to spawn and how to distribute the iteration space among the tasks (and more) can be configured via `@set` statements in the loop body.

Supports reductions (`@set reducer=<reducer function>`) and collecting the results (`@set collect=true`).

Under the hood, the `for` loop is translated into corresponding parallel [`tforeach`](@ref), [`tmapreduce`](@ref), or [`tmap`](@ref) calls.

See also: [`@set`](@ref), [`@local`](@ref)

## Examples

```julia
using OhMyThreads: @tasks
```

```julia
@tasks for i in 1:3
    println(i)
end
```

```julia
@tasks for x in rand(10)
    @set reducer=+
    sin(x)
end
```

```julia
@tasks for i in 1:5
    @set collect=true
    i^2
end
```

```julia
@tasks for i in 1:100
    @set ntasks=4*nthreads()
    # non-uniform work...
end
```

```julia
@tasks for i in 1:5
    @set scheduler=:static
    println("i=", i, " → ", threadid())
end
```

```julia
@tasks for i in 1:100
    @set begin
        scheduler=:static
        chunksize=10
    end
    println("i=", i, " → ", threadid())
end
```
