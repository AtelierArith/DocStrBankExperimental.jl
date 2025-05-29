```
convolution_power(a::Vector{<:Number}, n::Integer)
```

Compute convolution `n`-th power of vector `a`.

# Examples

```julia-repl
julia> a = [1, 2, 3]; convolution_power(a, 3)
7-element Vector{Int64}:
  1
  6
 21
 44
 63
 54
 27
```
