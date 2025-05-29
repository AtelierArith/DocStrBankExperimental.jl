```
x_table = get_x_table(x_info::Vector{StateElementInfo})
```

状態要素情報をDataFrames.DataFrameテーブルとして返します。例えば、次のように表示します：

```
show(x_table, allrows=true, allcols=true, summary=false, eltypes=false)
```
