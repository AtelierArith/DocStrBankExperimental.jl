Companion(v::Union{AbstractVector,Polynomial})::AbstractMatrix

特性（単項）多項式の係数から遅延 [`companion` 行列](https://en.wikipedia.org/wiki/Companion_matrix) を構築します。

行列は、長さ `n` のベクトル入力または次数 `n` の入力 `Polynomial` に対して `n × n` ですが、ここでのストレージは `O(n)` のみです。このバージョンでは、係数が行列の最後の列に配置されます。一部の文献では、係数が最初の行に配置されており、ここで使用されている慣習の転置です。

この型には `mul!` と `inv` のための効率的なメソッドがあります。

```jldoctest
julia> A = Companion([3,2,1])
3×3 Companion{Int64}:
 0  0  -3
 1  0  -2
 0  1  -1
```

また、多項式から直接：

```jldoctest
julia> using Polynomials

julia> P = Polynomial(2:5)
Polynomial(2 + 3*x + 4*x^2 + 5*x^3)

julia> C = Companion(P)
3×3 Companion{Float64}:
 0.0  0.0  -0.4
 1.0  0.0  -0.6
 0.0  1.0  -0.8
```
