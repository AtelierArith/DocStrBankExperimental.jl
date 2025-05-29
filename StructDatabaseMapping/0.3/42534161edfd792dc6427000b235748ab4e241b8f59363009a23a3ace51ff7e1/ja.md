```
function delete!(mapper::DBMapper, T::Type{<:Model}; kwargs...)
```

データベースから要素を削除します

# 引数

  * `mapper::DBMapper`: データベースマッパー
  * `T::DataType`: 削除したい登録モデルのデータ型
  * `kwargs`: 存在を検索したいフィールド。

```
struct Author <: Model ... end
delete!(mapper, Author, name="some name", age=30)
```
