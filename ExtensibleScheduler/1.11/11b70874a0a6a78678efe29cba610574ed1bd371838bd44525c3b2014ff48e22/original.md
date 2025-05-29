```
Action(func, args...; kwargs...)
```

An `Action` is a structure (a functor in fact) which stores function, arguments and keyword arguments.

An `Action` can be run (in fact it's run internally by a scheduler when a `Job` is triggered.)
