```
function select_one(mapper::DBMapper, T::Type{<:Model}; kwargs...)
```

データベースから1つの要素を選択します

# 引数

  * `mapper::DBMapper`: データベースマッパー
  * `T::DataType`: 選択したい登録モデルのデータ型
  * `kwargs`: 検索したいフィールド。パラメータpkは構造体の主キーを特定するための一般的な方法として使用できます

```
struct Author <: Model ... end
select_one(mapper, Author, name="Borges")       
```
