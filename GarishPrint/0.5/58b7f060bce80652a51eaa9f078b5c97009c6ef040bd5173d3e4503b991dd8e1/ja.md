```
pprint([io::IO=stdout], [mimetype], x; kw...)
```

オブジェクト `x` を `io` にきれいに印刷します。デフォルトの `io` は `stdout` です。

!!! note
    `pprint` はオブジェクトタイプが `Base.show` をオーバーロードしているかどうかを検出し、可能であればそれを使用します。カスタムタイプの `Base.show` を `GarishPrint` にオーバーロードする場合は、再帰的に `Base.show` に呼び出すのを避けるために [`pprint_struct`](@ref) を使用する必要があります。


# キーワード引数

  * `indent::Int`: インデントサイズ、デフォルトは `2` です。
  * `compact::Bool`: 一行で印刷するかどうか、デフォルトは `get(io, :compact, false)` です。
  * `limit::Bool`: 印刷が制限されているかどうか、デフォルトは `get(io, :compact, false)` です。
  * `displaysize::Tuple{Int, Int}`: 印刷された文字列の表示サイズのヒント、これは厳密には遵守されません。デフォルトは `displaysize(io)` です。
  * `show_indent::Bool`: インデントのヒントを印刷するかどうか、デフォルトは `true` です。
  * `color::Bool`: 色付きで印刷するかどうか、デフォルトは `true` です。

## 設定によって定義されたオプション構造体のキーワード引数

  * `include_defaults::Bool`: デフォルト値を印刷するかどうか、デフォルトは `false` で、REPL でのよりコンパクトな印刷を提供します。

## 色の好み

色の好みは、デフォルトのカラースキームをオーバーライドするためのキーワード引数として利用可能です。これらの引数は、`：normal`、`：default`、`：bold`、`：black`、`：blink`、`：blue`、`：cyan`、`：green`、`：hidden`、`：light_black`、`：light_blue`、`：light_cyan`、`：light_green`、`：light_magenta`、`：light_red`、`：light_yellow`、`：magenta`、`：nothing`、`：red`、`：reverse`、`：underline`、`：white`、または `：yellow`、または 0 から 255 の間の整数を取ることができます。すべての端末が 256 色をサポートしているわけではないことに注意してください。

デフォルトのカラースキームは、256 色用の `GarishPrint.default_colors_256()` と ANSI 色用の `GarishPrint.default_colors_ansi()` を介して確認できます。端末が 256 色をサポートしていると検出された場合、256 色が使用されます。

  * `fieldname`: 構造体のフィールド名。
  * `type`: 型の色。
  * `operator`: 演算子の色、例 `+`、`=>`。
  * `literal`: リテラルの色。
  * `constant`: 定数の色、例 `π`。
  * `number`: 数字の色、例 `1.2`、`1`。
  * `string`: 文字列の色。
  * `comment`: コメント、例 `# some comments`
  * `undef`: `UndefInitializer` への定数バインディング
  * `linenumber`: 行番号。

# 注意事項

色付き印刷とコンパクト印刷は、`IOContext` を設定することでオン/オフを切り替えることもできます。例えば、`IOContext(io, :color=>false)` は色なしで印刷し、`IOContext(io, :compact=>true)` は一行で印刷します。これは、標準の Julia `IO` オブジェクトがデフォルトで印刷する際の動作でもあります。
