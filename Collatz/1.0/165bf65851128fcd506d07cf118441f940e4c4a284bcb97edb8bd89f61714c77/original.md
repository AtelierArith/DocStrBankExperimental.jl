```
collatz_function(n; P=2, a=3, b=1)
```

Returns the output of a single application of a Collatz-esque function.

# Args

  * `n::Integer`: The value on which to perform the Collatz-esque function

# Kwargs

  * `P::Integer=2`: Modulus used to devide n, iff n is equivalent to (0 mod P).
  * `a::Integer=3`: Factor by which to multiply n.
  * `b::Integer=1`: Value to add to the scaled value of n.

# Examples

```jldoctest
julia> collatz_function(5)
16
```

```jldoctest
julia> collatz_function(14, P=7)
2
```

```jldoctest
julia> collatz_function(15, P=7, a=5, b=3)
78
```
