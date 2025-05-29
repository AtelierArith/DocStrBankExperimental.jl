```
function optimize(graphs::Union{Tuple,AbstractVector{<:AbstractGraph}}; level=0, verbose=0, normalize=nothing)

与えられた `graphs` のコピーを最適化します。重複したノードを削除し（`level > 0` の場合）、リーフを削除し、チェーンをフラットにし、線形結合をマージし、ゼロ値のサブグラフを削除します。
```

# 引数:

  * `graphs`: グラフのタプルまたはベクター。
  * `level`: 最適化レベル（デフォルト: 0）。0より大きい値は、重複したノードの削除など、より広範で遅い最適化プロセスをトリガーします。
  * `verbose`: 冗長性のレベル（デフォルト: 0）。
  * `normalize`: グラフを正規化するためのオプション関数（デフォルト: 何も指定しない）。

# 戻り値:

  * 最適化されたグラフのタプル/ベクター。
