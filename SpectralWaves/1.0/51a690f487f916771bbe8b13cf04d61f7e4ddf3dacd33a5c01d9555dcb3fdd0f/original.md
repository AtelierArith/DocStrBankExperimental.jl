```
convolve(a::Vector{Ta}, b::Vector{Tb}) where {Ta<:Number, Tb<:Number}
```

Compute direct convolution of vectors `a` and `b`.

# Examples

```julia-repl
julia> a = [1, 2]; b = [1, 1]; convolve(a, b)
3-element Vector{Int64}:
 1
 3
 2
```
