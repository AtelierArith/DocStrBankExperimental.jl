```
check_columns(checkset::CheckSet, check_name::String)::Vector{Symbol}
```

特定の名前付きチェックの列名を取得します。

# 引数

  * `checkset::CheckSet`: チェックセットオブジェクト。
  * `check_name::String`: 列名を取得する特定のチェックの名前。

# 戻り値

指定されたチェックで使用される列名のベクトル。

# 例

```julia
columns = check_columns(checkset, "column_type_check")  # Returns [:a, :b]
```
