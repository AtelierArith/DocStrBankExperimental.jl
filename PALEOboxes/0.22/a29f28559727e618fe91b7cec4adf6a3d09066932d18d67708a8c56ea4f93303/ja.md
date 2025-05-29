```
ModelData(model::Model; arrays_eltype::DataType=Float64, allocatenans::Bool=true)
```

`model` データ配列を含む ModelData 構造体を作成します。

データ配列の1セットは `eltype=arrays_eltype` で作成され、`arrays_idx=1` でアクセスされます。

追加のデータ配列セットは [`push_arrays_data!`](@ref) によって追加できます。例えば、配列要素型として Dual 数を必要とする自動微分をサポートするためです。

# フィールド

  * `cellranges_all::Vector{AbstractCellRange}`: すべてのドメインをカバーするデフォルトのセル範囲
  * `dispatchlists_all`: すべてのドメインをカバーするデフォルトのディスパッチリスト
  * `solver_view_all`: 外部ソルバーによって使用されるオプションの型なしコンテキストフィールド。
