```
pivottable(pt::PivotTable; columns::Union{Vector{Cell}, Nothing} = nothing,
           rows::Union{Vector{Cell}, Nothing} = nothing,
           values::Union{Vector{Value}, Nothing} = nothing,
           filters::Union{Vector{Filter}, Nothing} = nothing)
```

指定された `PivotTable` オブジェクト `pt` からピボットテーブルを作成します。

# 引数

  * `pt::PivotTable`: データを含むピボットテーブルオブジェクト。
  * `columns::Union{Vector{Cell}, Nothing}`: オプション。ピボットテーブルに含める列のベクター。指定されていない場合は `columns(pt)` にデフォルト設定されます。
  * `rows::Union{Vector{Cell}, Nothing}`: オプション。ピボットテーブルに含める行のベクター。指定されていない場合は `rows(pt)` にデフォルト設定されます。
  * `values::Union{Vector{Value}, Nothing}`: オプション。ピボットテーブルに含める値のベクター。指定されていない場合は `values(pt)` にデフォルト設定されます。
  * `filters::Union{Vector{Filter}, Nothing}`: オプション。ピボットテーブルに適用するフィルターのベクター。指定されていない場合は `filters(pt)` にデフォルト設定されます。

# 戻り値

  * 指定された列、行、値、およびフィルターを使用して作成されたピボットテーブル。
