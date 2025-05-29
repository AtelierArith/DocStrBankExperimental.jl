```
summarize_table(s::Symbol) -> summary::DataFrame
```

テーブル`s`の要約を返します。`summary_table`には、`summarize_table`からのすべての情報に加えて、指定された追加の列を含むすべてのテーブルの要約が含まれるため、より多くの情報を提供できます。

関連情報としては、[`get_table(data, name)`](@ref)、[`read_summary_table!(config, data)`](@ref)、[`get_table_summary(data, name)`](@ref)があります。
