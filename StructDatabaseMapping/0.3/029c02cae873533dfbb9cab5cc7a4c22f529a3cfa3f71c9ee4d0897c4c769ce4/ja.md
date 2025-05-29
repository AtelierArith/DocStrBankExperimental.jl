```
function exists(mapper::DBMapper, elem::T) where T<:Model
```

要素がデータベースに存在するかどうかを返します

# 引数

  * `mapper::DBMapper`: データベースマッパー
  * `elem<:Model`: 存在を確認する要素

```
struct Author <: Model ... end
exists(mapper, Author(name="some name", age=30))
```
