`fakedegrees(W, q=Pol())`

は、ベクトル空間 `V` 上の反射群 `W` のフェイク次数を保持するリストを返します。これは、`SV` が `V` の対称代数であり、`I` が `SV` の正の次数の同次不変量によって生成される理想であるとき、商 `SV/I` における `W` の不可約キャラクターのグレード付き重複度です。結果の順序は、`charinfo(W)` におけるキャラクターの順序に対応しています。

```julia-repl
julia> fakedegrees(coxgroup(:A,2),Pol(:q))
3-element Vector{Pol{Int64}}:
 q³
 q²+q
 1
```
