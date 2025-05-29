```
convergents(a::T, b::T) where T <: Integer
```

Return the convergents of a rational `a/b`.

# Example

```julia
julia> convergents(31, 73)
6-element Array{Rational,1}:
  0//1
  1//2
  2//5
  3//7
 14//33
 31//73
```
