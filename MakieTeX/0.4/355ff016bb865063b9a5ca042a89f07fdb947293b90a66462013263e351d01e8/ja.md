```
TypstDocument(contents::AbstractString, add_defaults::Bool; preamble)
```

このコンストラクタ関数は、`TypstDocument`型の`struct`を作成します。すべての引数は文字列として渡される必要があります。

`add_defaults`が`false`の場合、ドキュメント構造は*自動的に*追加されません。この場合、キーワード引数は無視され、`contents`は完全なTypstドキュメントでなければなりません。

利用可能なキーワード引数は次のとおりです：

  * `preamble`: `contents`の前に挿入される任意のコード。デフォルト: `""`。

他に[`CachedTypst`](@ref)、[`compile_typst`](@ref)なども参照してください。
