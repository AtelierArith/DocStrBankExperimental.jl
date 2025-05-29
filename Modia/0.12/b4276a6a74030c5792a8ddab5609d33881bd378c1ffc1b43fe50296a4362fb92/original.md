```
x_table = get_x_table(x_info::Vector{StateElementInfo})
```

Return the state element info as DataFrames.DataFrame table, for example to print it as:

```
show(x_table, allrows=true, allcols=true, summary=false, eltypes=false)
```
