```julia
IncidenceMatrix(sys)

```

システムのインシデンス行列を構築し、実際の行列およびその他の関連値を評価します。

# 引数

  * `sys::PSY.System`:       考慮すべきパワーシステム
  * `reduce_radial_branches::Bool`:       Trueの場合、行列はすべての放射状ブランチとリーフバスを無視して評価されます（オプション、デフォルト値はfalse）
