`col_hermite_transforms(m::AbstractMatrix{<:Integer})`

整数行列 `m` の列ヘルミート標準形 `H` は、列同値の下三角形です。*ピボット*は、`H` の列の最初の非ゼロエントリであり（ピボットの右上の象限はゼロ）、ピボットは正であり、ピボットの左のエントリは非負であり、ピボットより小さいです。行列 `m*c==H` を満たす一意のユニモジュラー行列 `c` が存在します。関数 `col_hermite_transforms` は、コンポーネント `.normal=H` と `.coltrans=c` を持つ名前付きタプルを返します。

```julia-repl
julia> m=[1 15 28;4 5 6;7 8 9]
3×3 Matrix{Int64}:
 1  15  28
 4   5   6
 7   8   9

julia> n=col_hermite_transforms(m)
(normal = [1 0 0; 0 1 0; 0 1 3], coltrans = [-1 13 -50; 2 -27 106; -1 14 -55], rank = 3, signdet = 1)

julia> m*n.coltrans==n.normal
true
```
