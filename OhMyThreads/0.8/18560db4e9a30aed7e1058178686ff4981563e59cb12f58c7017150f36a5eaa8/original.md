```
tmap!(f, out, A::AbstractArray...;
      [scheduler::Union{Scheduler, Symbol} = :dynamic])
```

A multithreaded function like `Base.map!`. In parallel on multiple tasks, this function assigns each element of `out[i] = f(A[i])` for each index `i` of `A` and `out`.

## Keyword arguments:

  * `scheduler::Union{Scheduler, Symbol}` (default `:dynamic`): determines how the computation is divided into parallel tasks and how these are scheduled. See [`Scheduler`](@ref) for more information on the available schedulers.

In addition, `tmap!` accepts **all keyword arguments that are supported by the selected scheduler**. They will simply be passed on to the corresponding `Scheduler` constructor. However, to avoid ambiguity, this is currently **only supported for `scheduler::Symbol`** (but not for `scheduler::Scheduler`).
