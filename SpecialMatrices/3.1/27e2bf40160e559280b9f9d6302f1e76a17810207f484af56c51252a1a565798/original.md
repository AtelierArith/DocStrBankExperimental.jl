```
Cauchy{T,X,Y} <: AbstractMatrix{T}
Cauchy(x [,y])
```

Construct lazy [`Cauchy` matrix](https://en.wikipedia.org/wiki/Cauchy_matrix) where

  * `Cauchy(x,y)[i,j] = 1 / (x[i] + y[j])`
  * `Cauchy(x) = Cauchy(x,x)`
  * `Cauchy(k::Int) = Cauchy(1:k)`

Both `x` and `y` can be any `AbstractArray` or `NTuple` of `Number`s, but all elements of `x` must have the same type; likewise for `y`. The elements of `x` and of `y` should be distinct.

The element type `T` corresponds to the reciprocal of the sum of pairs of elements of `x` and `y`.

```jldoctest
julia> Cauchy([2.0 1], (0, 1, 2))
2×3 Cauchy{Float64, Matrix{Float64}, Tuple{Int64, Int64, Int64}}:
 0.5  0.333333  0.25
 1.0  0.5       0.333333

julia> Cauchy(1:3)
3×3 Cauchy{Rational{Int64}, UnitRange{Int64}, UnitRange{Int64}}:
 1//2  1//3  1//4
 1//3  1//4  1//5
 1//4  1//5  1//6

julia> Cauchy(3)
3×3 Cauchy{Rational{Int64}, UnitRange{Int64}, UnitRange{Int64}}:
 1//2  1//3  1//4
 1//3  1//4  1//5
 1//4  1//5  1//6
```
