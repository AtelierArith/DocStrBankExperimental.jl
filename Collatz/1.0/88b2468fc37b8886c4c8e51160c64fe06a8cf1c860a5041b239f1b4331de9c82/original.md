```
hailstone_sequence(initial_value; P=2, a=3, b=1, max_total_stopping_time=1000, total_stopping_time=true, verbose=true)
```

Returns a list of successive values obtained by iterating a Collatz-esque function.

Until either 1 is reached, or the total amount of iterations exceeds max*total*stopping*time. Unless total*stopping_time is False, which will terminate the hailstone at the "stopping time" value, i.e. the first value less than the initial value. While the sequence has the capability to determine that it has encountered a cycle, the cycle from "1" wont be attempted or reported as part of a cycle, regardless of default or custom parameterisation, as "1" is considered a "total stop".

# Args

  * `initial_value::Integer`: The value to begin the hailstone sequence from.

# Kwargs

  * `P::Integer=2`: Modulus used to devide n, iff n is equivalent to (0 mod P).
  * `a::Integer=3`: Factor by which to multiply n.
  * `b::Integer=1`: Value to add to the scaled value of n.
  * `max_total_stopping_time::Integer=1000`: Maximum amount of times to iterate the   function, if 1 is not reached.
  * `total_stopping_time::Bool=true`: Whether or not to execute until the "total"   stopping time (number of iterations to obtain 1) rather than the regular stopping   time (number of iterations to reach a value less than the initial value).
  * `verbose::Bool=true`: If set to verbose, the hailstone sequence will include   control string sequences to provide information about how the sequence   terminated, whether by reaching a stopping time or entering a cycle.

# Examples

```jldoctest
julia> print(hailstone_sequence(16, verbose=false))
[16, 8, 4, 2, 1]
```

```jldoctest
julia> print(hailstone_sequence(16))
Any[16, 8, 4, 2, 1, Any[Collatz._CC.TOTAL_STOPPING_TIME, 4]]
```

```jldoctest
julia> print(hailstone_sequence(761, P=5, a=2, b=3, verbose=false))
[761, 1525, 305, 61, 125, 25, 5, 1]
```

# Example cycle!

```jldoctest
julia> print(hailstone_sequence(-56))
Any[-56, -28, Collatz._CC.CYCLE_INIT, Any[-14, -7, -20, -10, -5], Any[Collatz._CC.CYCLE_LENGTH, 5]]
```

```jldoctest
julia> print(hailstone_sequence(-56, verbose=false))
[-56, -28, -14, -7, -20, -10, -5, -14]
```
