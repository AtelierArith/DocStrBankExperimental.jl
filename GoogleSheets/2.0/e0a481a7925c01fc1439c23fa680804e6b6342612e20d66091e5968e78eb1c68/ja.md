```
DataFrame(values::CellRangeValues)::Union{Nothing,DataFrame}
```

スプレッドシートの範囲値からDataFrameを作成します。最初の行は列名に変換されます。他のすべての行は文字列値に変換されます。

# 引数

  * `values::CellRangeValues`: セルの値
