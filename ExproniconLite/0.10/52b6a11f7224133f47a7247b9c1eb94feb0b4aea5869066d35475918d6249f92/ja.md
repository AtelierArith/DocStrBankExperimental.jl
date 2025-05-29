```
mutable struct JLKwField <: JLExpr
```

タイプは、Julia構造体内でデフォルト値を持つことができるJuliaフィールドを説明します。

```
JLKwField(;kw...)
```

`JLKwField`インスタンスを作成します。

# フィールドとキーワード引数

以下のすべてのフィールドは、コンストラクタ内のキーワード引数`kw`として有効であり、`<object>.<field>`を介してアクセスできます。

コンストラクタに必要な唯一のキーワード引数は`name`であり、残りはすべてオプションです。

  * `name::Symbol`: フィールドの名前。
  * `type`: フィールドの型。
  * `isconst`: フィールドが`const`で注釈されているかどうか。
  * `default`: フィールドのデフォルト値、デフォルトは[`no_default`](@ref)です。
  * `line::LineNumberNode`: 行情報を示すための`LineNumberNode`。
  * `doc::String`: この定義のドキュメント文字列。
