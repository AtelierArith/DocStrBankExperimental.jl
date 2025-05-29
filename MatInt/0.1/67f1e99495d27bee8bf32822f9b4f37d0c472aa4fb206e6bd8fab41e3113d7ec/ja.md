`hermite_transforms(m::AbstractMatrix{<:Integer})`

行のエルミート正規形 `H` は、同じ整数の行空間を持つ上三角形の形です。さらに、この形では、*ピボット* が `H` の行の最初の非ゼロエントリである場合、ピボットの左下の象限はゼロであり、ピボットは正であり、ピボットの上のエントリは非負であり、ピボットより小さいです。`m` がフルランクである場合、ユニモジュラー行列 `r` が存在し、`r*m==H` となります。関数 `hermite_transforms` は、コンポーネント `.normal=H` と `.rowtrans=r` を持つ名前付きタプルを返します。

```julia-repl
julia> m=[1 15 28;4 5 6;7 8 9]
3×3 Matrix{Int64}:
 1  15  28
 4   5   6
 7   8   9

julia> n=hermite_transforms(m)
(normal = [1 0 1; 0 1 1; 0 0 3], rowtrans = [-2 62 -35; 1 -30 17; -3 97 -55], rank = 3, signdet = 1)

julia> n.rowtrans*m==n.normal
true
```
