```
render(value;
    input = "input.typ",
    output = "output.pdf",
    open = true,
    ignorestatus = true,
    preamble = preamble,
context...)
```

[`show(::IO, ::MIME"text/typst", ::Typst)`](@ref)を使用して文書をレンダリングします。

これにより、最初に[`preamble`](@ref)とフォーマットされた`value`を含む`input`ファイルが生成されます。次に、それは`output`文書にコンパイルされ、その形式はファイル拡張子から`pdf`、`png`、または`svg`であると推測されます。文書はデフォルトのビューアによって自動的に`open`される場合があります。[`ignorestatus`](@ref)フラグを設定することができます。これにより、[`julia_mono`](@ref)フォントを使用することがサポートされます。

# 例

```jldoctest
julia> render(Any[true 1; 1.2 1 // 2]);
```
