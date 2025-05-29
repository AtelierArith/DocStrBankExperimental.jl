```
RenderableText(text::String; width::Union{Nothing, Int, Symbol}=nothing)
```

文字列から `RenderableText` を構築します。

テキストは指定された幅に合わせてサイズ変更されます。オプションで `justify` を使用してテキストの整列スタイルを設定できます ∈ (:left, :center, :right, :justify)。
