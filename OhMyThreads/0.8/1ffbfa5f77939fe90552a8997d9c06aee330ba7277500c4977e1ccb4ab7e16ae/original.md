```
tcollect([OutputElementType], gen::Union{AbstractArray, Generator{<:AbstractArray}};
         [scheduler::Union{Scheduler, Symbol} = :dynamic])
```

A multithreaded function like `Base.collect`. Essentially just calls `tmap` on the generator function and inputs.

The optional argument `OutputElementType` will select a specific element type for the returned container, and will generally incur fewer allocations than the version where `OutputElementType` is not specified.

## Example:

```
using OhMyThreads: tcollect

tcollect(sin(i) for i in 1:10)
```

## Keyword arguments:

  * `scheduler::Union{Scheduler, Symbol}` (default `:dynamic`): determines how the computation is divided into parallel tasks and how these are scheduled. See [`Scheduler`](@ref) for more information on the available schedulers.

In addition, `tcollect` accepts **all keyword arguments that are supported by the selected scheduler**. They will simply be passed on to the corresponding `Scheduler` constructor. Example:

```
tcollect(sin(i) for i in 1:10; chunksize=2, scheduler=:static)
```

However, to avoid ambiguity, this is currently **only supported for `scheduler::Symbol`** (but not for `scheduler::Scheduler`).
