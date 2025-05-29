```
wignerseitz(basis::AbstractVector{<:SVector{D}}; merge::Bool = true, Nmax = 3)
wignerseitz(basis::AbstractVector{<:AbstractVector}; merge::Bool = true, Nmax = 3)
                                                            --> Cell{D}
```

提供された基底に基づいて、`D` 次元で `basis` によって定義されたウィグナー-ザイツセルの頂点と関連する（外向きの）面を含む `Cell{D}` を返します。返される頂点は `basis` の基底で与えられます（変換については [`cartesianize!`](@ref) を参照してください）。

## キーワード引数

  * `merge`（デフォルトは `true`）：`true` の場合、共平面の面が統合されて多角形の平面面（例：三角形、四角形、一般的な n 辺形）を形成します。`false` の場合、生の「未処理」の三角形（`D=3`）とセグメント（`D=2`）が返されます。`D=1` の場合、`merge` は影響を与えません。
  * `Nmax`（デフォルトは `3`）：基礎となるボロノイ分割を生成するために使用される初期格子に `-Nmax:Nmax` の点を含めます。収束を明示的にテストせずにこれを 3 未満に設定するのは賢明ではなく、3 を超えて増やす必要もおそらくありません。
