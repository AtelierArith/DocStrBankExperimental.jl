```
@process f(arg...) [cycles]
```

Create a process from a function `f(arg...)`.

Wrap a function and its arguments in a [`Prc`](@ref) and start it with  [`process!`](@ref).

# Arguments

  * `f`: a function,
  * `arg...`: arguments, the first argument must be an AbstractClock,
  * `cycles::Int`: the number of cycles, `f` should run.

# Returns

  * an `Int` process id.
