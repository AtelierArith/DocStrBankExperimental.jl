```
Cauchy{T,X,Y} <: AbstractMatrix{T}
Cauchy(x [,y])
```

遅延構築された [`Cauchy` 行列](https://en.wikipedia.org/wiki/Cauchy_matrix) を作成します。ここで、

  * `Cauchy(x,y)[i,j] = 1 / (x[i] + y[j])`
  * `Cauchy(x) = Cauchy(x,x)`
  * `Cauchy(k::Int) = Cauchy(1:k)`

`x` と `y` は任意の `AbstractArray` または `Number` の `NTuple` であることができますが、`x` のすべての要素は同じ型でなければなりません。同様に `y` もそうです。`x` と `y` の要素は異なるべきです。

要素型 `T` は、`x` と `y` の要素のペアの合計の逆数に対応します。

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
