```
@krecord struct MyStruct
    a::Int = 1
    b::Float64
end
```

キーワード引数を持つ構造体を定義するためのマクロと `MLStyle.@as_record`、および次の汎用関数が定義されています：

  * `copy`
