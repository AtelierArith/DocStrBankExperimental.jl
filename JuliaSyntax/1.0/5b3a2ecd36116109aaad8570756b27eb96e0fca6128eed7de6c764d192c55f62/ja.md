```
highlight(io, x; color, note, notecolor,
          context_lines_before, context_lines_inner, context_lines_after)

highlight(io::IO, source::SourceFile, range::UnitRange; kws...)
```

`x`を強調表示した背景`color`でハイライトし、テキスト内のマーカーで下線を引いた周囲のソースコードの行を印刷します。注釈として`notecolor`の`note`を提供することができます。デフォルトでは、`x`は`sourcefile(x)`と`byte_range(x)`が実装されたオブジェクトである必要があります。

コンテキスト引数`context_lines_before`などは、前後に印刷されるコード行の数を指し、`inner`はマルチライン領域内のコンテキスト行を指します。

2番目の形式は最初の形式のキーワードを共有しますが、明示的なソースファイルとバイト範囲を指定することができます。
