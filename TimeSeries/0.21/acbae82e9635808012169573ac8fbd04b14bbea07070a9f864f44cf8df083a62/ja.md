```
merge(ta1::TimeArray{T}, ta2::TimeArray{T}, [tas::TimeArray{T}...];
      method = :inner, colnames = [...], padvalue = NaN)
```

複数の `TimeArray` を時間インデックスに沿ってマージします。

## 引数

  * `method::Symbol`: `:inner`、`:outer`、`:left` または `:right`。
