```
@add_arg_table!(settings, table...)
```

このマクロは、指定された `settings` に引数とオプションのテーブルを追加します。複数回呼び出すことができます。引数グループは自動的に決定されるか、指定された場合は現在のデフォルトグループが使用されます（詳細については [Argument groups](@ref) セクションを参照してください）。

`table` は、各要素が `String`、または `String` のタプルまたはベクター、または代入式、またはブロックであるリストです：

  * `String`、タプル、またはベクターは、新しい位置引数またはオプションを導入します。タプルとベクターはオプションまたはコマンドにのみ許可され、代替名を提供します（例： `["--opt", "-o"]` または `["checkout", "co"]`）
  * 代入式（すなわち `=`、 `:=` または `=>` を使用する式）は、前の引数の動作を説明します（例： `help = "an option"` または `required => false`）。完全な説明については [Argument entry settings](@ref) セクションを参照してください。
  * ブロック（`begin...end` またはセミコロンで区切られた式のリスト）は、エントリをグループ化し、複数行にまたがるのに便利です。

これらのルールにより、さまざまな使用スタイルが可能になり、[Argument table styles](@ref) セクションで議論されています。ドキュメントの残りの部分では、主にこのスタイルを使用します：

```julia
@add_arg_table! settings begin
    "--opt1", "-o"
        help = "an option with an argument"
    "--opt2"
    "arg1"
        help = "a positional argument"
        required = true
end
```

上記の例では、`table` は単一の `begin...end` ブロックに置かれ、行 `"--opt1", "-o"` はタプルとして解析されます。インデントは可読性を助けるために使用されています。

関数 [`add_arg_table!`](@ref) も参照してください。
