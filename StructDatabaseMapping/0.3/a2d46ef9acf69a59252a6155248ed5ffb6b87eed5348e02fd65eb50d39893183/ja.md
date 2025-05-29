```
function drop_table!(mapper::DBMapper, T::DataType)
```

DBから構造体データを（可能な場合に）削除します

# 引数

  * `mapper::DBMapper`: データベースマッパー
  * `T::Type{<:Model}`: 登録されたモデルのデータ型
