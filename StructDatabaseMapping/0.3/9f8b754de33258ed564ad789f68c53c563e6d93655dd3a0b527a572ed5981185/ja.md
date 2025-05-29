```
function delete!(mapper::DBMapper, T::Type{<:Model}; kwargs...)
```

データベースから要素を削除します

# 引数

  * `mapper::DBMapper`: データベースマッパー
  * `elem<:Model`: 削除する要素

要素には有効な識別子が必要です。

```
struct Author <: Model ... end
delete!(mapper, Author(id=valid_id, name="some name", age=30))
```
