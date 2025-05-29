```
AbstractOutputWriter
```

PALEOモデル出力のためのコンテナによって実装されるインターフェース。

実装は以下のメソッドを定義する必要があります：

# 出力の書き込み

  * [`initialize!`](@ref)
  * [`add_record!`](@ref)

# 出力の修正

  * [`PB.add_field!`](@ref)

# 出力のクエリ

  * [`PB.get_table`](@ref)
  * [`PB.show_variables`](@ref)
  * [`PB.has_variable`](@ref)

# 出力データへのアクセス

  * [`PALEOmodel.get_array`](@ref)
  * [`PB.get_field`](@ref)
  * [`PB.get_mesh`](@ref)
  * [`PB.get_data`](@ref)
