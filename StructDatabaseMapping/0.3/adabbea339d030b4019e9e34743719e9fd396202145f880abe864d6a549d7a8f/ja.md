```
function create_table(mapper::DBMapper, T::Type{<:Model}; if_not_exists::Bool=true)
```

指定されたモデルのためのテーブルを作成します。
