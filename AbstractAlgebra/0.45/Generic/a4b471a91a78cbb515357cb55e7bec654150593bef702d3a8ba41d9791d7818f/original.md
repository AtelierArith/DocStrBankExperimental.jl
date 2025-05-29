```
^(g::Perm, n::Integer)
```

Return the $n$-th power of a permutation `g`.

By default `g^n` is computed by cycle decomposition of `g` if `n > 3`. `Generic.power_by_squaring` provides a different method for powering which may or may not be faster, depending on the particular case. Due to caching of the cycle structure, repeated powering of `g` will be faster with the default method.

# Examples

```jldoctest
julia> g = Perm([2,3,4,5,1])
(1,2,3,4,5)

julia> g^3
(1,4,2,5,3)

julia> g^5
()
```
