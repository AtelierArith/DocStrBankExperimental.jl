```
mutable struct JLField <: JLExpr
JLField(;kw...)
```

TypeはJuliaの構造体におけるJuliaフィールドを説明します。

# フィールドとキーワード引数

以下のすべてのフィールドは、コンストラクタのキーワード引数`kw`として有効であり、`<object>.<field>`を介してアクセスできます。

コンストラクタに必要な唯一のキーワード引数は`name`であり、残りはすべてオプションです。

  * `name::Symbol`: フィールドの名前。
  * `type`: フィールドの型。
  * `isconst`: フィールドが`const`で注釈されているかどうか。
  * `line::LineNumberNode`: 行情報を示すための`LineNumberNode`。
  * `doc::String`: この定義のドキュメント文字列。
