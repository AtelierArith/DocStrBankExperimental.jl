```
stopping_time(initial_value; P=2, a=3, b=1, max_stopping_time=1000, total_stopping_time=false)
```

Returns the stopping time, the amount of iterations required to reach a value less than the initial value, or nothing if max*stopping*time is exceeded.

Alternatively, if total*stopping*time is True, then it will instead count the amount of iterations to reach 1. If the sequence does not stop, but instead ends in a cycle, the result will be infinity. If (P,a,b) are such that it is possible to get stuck on zero, the result will be the negative of what would otherwise be the "total stopping time" to reach 1, where 0 is considered a "total stop" that should not occur as it does form a cycle of length 1.

# Args

  * `initial_value::Integer`: The value for which to find the stopping time.

# Kwargs

  * `P::Integer=2`: Modulus used to devide n, iff n is equivalent to (0 mod P).
  * `a::Integer=3`: Factor by which to multiply n.
  * `b::Integer=1`: Value to add to the scaled value of n.
  * `max_stopping_time::Integer=1000`: Maximum amount of times to iterate the function, if the stopping   time is not reached. IF the max*stopping*time is reached, the function will return nothing.
  * `total_stopping_time::Bool=false`: Whether or not to execute until the "total"   stopping time (number of iterations to obtain 1) rather than the regular   stopping time (number of iterations to reach a value less than the initial value).

# Examples

```jldoctest
julia> stopping_time(5)
3
julia> stopping_time(27)
96
julia> stopping_time(21, P=5, a=2, b=3, total_stopping_time=true)
Inf
```
