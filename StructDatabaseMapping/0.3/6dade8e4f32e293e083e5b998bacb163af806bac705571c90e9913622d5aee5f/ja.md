```
select_all(mapper::DBMapper, T::Type{<:Model}; ; fields::Array{Symbol}=[], kwargs...)
```

条件を満たすすべての要素を選択します

# 引数

  * `mapper::DBMapper`: データベースマッパー
  * `T::DataType`: 検索したい登録モデルのデータ型
  * `kwargs`: 検索したい条件

```
struct Author <: Model ... end
select_all(mapper, Author, age=30)
```
