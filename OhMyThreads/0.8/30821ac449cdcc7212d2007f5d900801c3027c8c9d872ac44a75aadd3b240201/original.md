```
treduce(op, A::AbstractArray...;
        [scheduler::Union{Scheduler, Symbol} = :dynamic],
        [outputtype::Type = Any],
        [init])
```

A multithreaded function like `Base.reduce`. Perform a reduction over `A` using the two-argument function `op`.

Note that `op` **must** be an [associative](https://en.wikipedia.org/wiki/Associative_property) function, in the sense that `op(a, op(b, c)) ≈ op(op(a, b), c)`. If `op` is not (approximately) associative, you will get undefined results.

## Example:

```
using OhMyThreads: treduce

treduce(+, [1, 2, 3, 4, 5])
```

is the parallelized version of `sum([1, 2, 3, 4, 5])` in the form

```
(1 + 2) + (3 + 4) + 5
```

## Keyword arguments:

  * `scheduler::Union{Scheduler, Symbol}` (default `:dynamic`): determines how the computation is divided into parallel tasks and how these are scheduled. See [`Scheduler`](@ref) for more information on the available schedulers.
  * `outputtype::Type` (default `Any`): will work as the asserted output type of parallel calculations. We use [StableTasks.jl](https://github.com/JuliaFolds2/StableTasks.jl) to make setting this option unnecessary, but if you experience problems with type stability, you may be able to recover it with this keyword argument.
  * `init`: initial value of the reduction. Will be forwarded to `mapreduce` for the task-local sequential parts of the calculation.

In addition, `treduce` accepts **all keyword arguments that are supported by the selected scheduler**. They will simply be passed on to the corresponding `Scheduler` constructor. Example:

```
treduce(+, [1, 2, 3, 4, 5]; chunksize=2, scheduler=:static)
```

However, to avoid ambiguity, this is currently **only supported for `scheduler::Symbol`** (but not for `scheduler::Scheduler`).
