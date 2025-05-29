`asreflection(s::Matrix [,r::AbstractVector])`

`s` は正方行列である必要があり、`r` が与えられた場合は `size(s,1)` の長さのベクトルである必要があります。この関数は、`s` が複素反射の行列であるかどうかを判断します（`r` が与えられた場合は、`r` の根の反射の行列であるかどうかを判断します；`r` を与える目的は、望ましい根とコルートを正確に指定することであり、そうでなければスカラーとその逆数までしか決定されません）。この関数は、`s` が反射でない場合（または `r` の根を持つ反射でない場合）には `nothing` を返し、そうでない場合は4つのフィールドを持つ名前付きタプルを返します：

`.root`:   反射 `s` の根（与えられた場合は `r` と等しい）

`.coroot`:  `s` のコルート

`.eigenvalue`:  `s` の非自明な固有値

`.isunitary`: `s` が通常のスカラー積に関してユニタリである場合にのみ `true` となるブール値（この場合、`s` は根と固有値によって `reflectionMatrix(.root,.eigenvalue)` として決定されます）

```julia-repl
julia> asreflection([-1 0 0;1 1 0;0 0 1])
(root = [2, 0, 0], coroot = Rational{Int64}[1, -1//2, 0], eig = -1, isunitary = false)

julia> asreflection([-1 0 0;1 1 0;0 0 1],[1,0,0])
(root = [1, 0, 0], coroot = Rational{Int64}[2, -1, 0], eig = -1, isunitary = false)
```
