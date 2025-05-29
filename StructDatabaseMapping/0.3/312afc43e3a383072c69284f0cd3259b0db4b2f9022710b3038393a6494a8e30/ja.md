```
clean_table!(mapper::DBMapper, T::Type{<:Model})
```

タイプ T のすべての要素を削除します。

# 引数

  * `mapper::DBMapper`: データベースマッパー
  * `T::Type{<:Model}`: 登録されたモデルのデータ型

可能な場合は、それらの要素が格納されている構造（リレーショナルケースのテーブル）を示します。
