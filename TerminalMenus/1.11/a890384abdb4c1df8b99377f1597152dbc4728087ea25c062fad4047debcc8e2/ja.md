```
MultiSelectMenu(options::Array{String,1}; pagesize::Int=10)
```

MultiSelectMenuオブジェクトを作成します。`request(menu::MultiSelectMenu)`を使用してユーザー入力を取得します。`request()`は、ユーザーによって選択されたオプションのインデックスを含む`Set`を返します。

# 引数

  * `options::Array{String, 1}`: 表示されるオプション
  * `pagesize::Int=10`: 一度に表示されるオプションの数。`length(options) > pagesize`の場合、メニューはスクロールします。
