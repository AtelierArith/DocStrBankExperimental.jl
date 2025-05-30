```
tforeach(f, A::AbstractArray...;
         [scheduler::Union{Scheduler, Symbol} = :dynamic]) :: Nothing
```

A multithreaded function like `Base.foreach`. Apply `f` to each element of `A` on multiple parallel tasks, and return `nothing`. I.e. it is the parallel equivalent of

```
for x in A
    f(x)
end
```

## Example:

```
using OhMyThreads: tforeach

tforeach(1:10) do i
    println(i^2)
end
```

## Keyword arguments:

  * `scheduler::Union{Scheduler, Symbol}` (default `:dynamic`): determines how the computation is divided into parallel tasks and how these are scheduled. See [`Scheduler`](@ref) for more information on the available schedulers.

In addition, `tforeach` accepts **all keyword arguments that are supported by the selected scheduler**. They will simply be passed on to the corresponding `Scheduler` constructor. Example:

```
tforeach(1:10; chunksize=2, scheduler=:static) do i
    println(i^2)
end
```

However, to avoid ambiguity, this is currently **only supported for `scheduler::Symbol`** (but not for `scheduler::Scheduler`).
