function exists(mapper::DBMapper, T::Type{T}; kwargs...) where T <: Model

データベースに要素が存在するかどうかを返します

# 引数

  * `mapper::DBMapper`: データベースマッパー
  * `T::DataType`: 存在を知りたい登録モデルのデータ型
  * `kwargs`: 存在を検索したいフィールド。パラメータ pk は構造体の主キーを特定するための一般的な方法として使用できます

```
struct Author <: Model ... end
exists(mapper, Author, name="some name", age=30)
```
