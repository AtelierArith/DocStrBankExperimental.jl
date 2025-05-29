```
Material(shelf, book, page) -> Union{Material, Vector{Material}}
```

材料の *shelf*、*book*、*page* をそれぞれ提供します。このメソッドは次に `Material("$shelf/$book/$page")` を呼び出します。

# 引数

  * `shelf::String` : 材料の棚
  * `book::String` : 材料の本
  * `page::String` : 材料のページ
