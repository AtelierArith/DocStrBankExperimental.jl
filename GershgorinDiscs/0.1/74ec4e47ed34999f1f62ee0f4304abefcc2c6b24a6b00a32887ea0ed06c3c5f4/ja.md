```
list_discs(A::AbstractMatrix)
```

正方行列のガーシュゴリン円を計算します。

各円は対角要素を中心に持ち、その半径はその要素の行和と列和の小さい方の値です。

# 引数

  * `A::AbstractMatrix`: 正方行列（実数または複素数）。

## 例

```jldoctest
julia> A = [4.0 1.0; 0.5 3.0]
2×2 Matrix{Float64}:
 4.0  1.0
 0.5  3.0

julia> list_discs(A)
2-element Vector{GershgorinDisc{Float64}}:
 GershgorinDisc{Float64}((4.0, 0.0), 0.5)
 GershgorinDisc{Float64}((3.0, 0.0), 0.5)
```
