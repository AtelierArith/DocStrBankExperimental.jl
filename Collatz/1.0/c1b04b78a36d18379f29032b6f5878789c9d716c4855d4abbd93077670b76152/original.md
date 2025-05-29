```
reverse_collatz_function(n; P=2, a=3, b=1)
```

Returns the output of a single application of a Collatz-esque reverse function.

# Args

  * `n::Integer`: The value on which to perform the reverse Collatz function

# Kwargs

  * `P::Integer=2`: Modulus used to devide n, iff n is equivalent to (0 mod P).
  * `a::Integer=3`: Factor by which to multiply n.
  * `b::Integer=1`: Value to add to the scaled value of n.

# Examples

```jldoctest
julia> print(reverse_collatz_function(1))
[2]
```

```jldoctest
julia> print(reverse_collatz_function(4))
[1, 8]
```

```jldoctest
julia> print(reverse_collatz_function(3, P=-3, a=-2, b=-5))
[-9, -4]
```
