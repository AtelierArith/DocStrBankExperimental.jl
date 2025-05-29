```
Prc(id, f, arg...; kw...)
Prc(f, arg...; kw...)
```

Prepare a function to run as a process and get registered to a clock.

# Arguments, Fields

  * `id`: some unique identification for registration,
  * `f::Function`: a function `f(clk, arg...; kw...)`, must take `clk`    (a [`Clock`](@ref)) as its first argument,
  * `arg...`: further arguments to `f`
  * `kw...`: keyword arguments to `f`

# Fields identified during registration

  * `id`: if it is not provided, some integer will be calculated    for it during registration,
  * `task::Union{Task,Nothing}`: a task structure used for diagnosis,
  * `clk::Union{AbstractClock,Nothing}`: clock where the process is    registered,

!!! note "The clock is identified dynamically!"
    The clock `clk` where a process runs and gets registered is identified during process startup and then passed as 1st  argument to `f`.

