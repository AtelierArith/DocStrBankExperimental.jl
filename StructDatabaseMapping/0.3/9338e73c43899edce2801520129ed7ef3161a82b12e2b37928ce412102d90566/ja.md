```
function update!(mapper::DBMapper, elem::T; fields::Array{Symbol}=Symbol[]) where T<:Model
```

データベースに要素を挿入します

# 引数

  * `mapper::DBMapper`: データベースマッパー
  * `elem::T where T<:Model`: 挿入するインスタンス化されたモデル
  * `fields::Array{Symbol}`: オプション。更新するフィールドの配列。

```
struct Author <: Model ... end
author = Author(name="some name", age=30)
update!(mapper, author)       
update!(mapper, author, fields=[:age])       
```
