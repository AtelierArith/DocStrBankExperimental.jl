```
savefig(
    p::Plot, fn::AbstractString;
    format::Union{Nothing,String}=nothing,
    width::Union{Nothing,Int}=nothing,
    height::Union{Nothing,Int}=nothing,
    scale::Union{Nothing,Real}=nothing,
)
```

プロット `p` を `fn` という名前のファイルに保存します。`format` が指定され、png、jpeg、webp、svg、pdf、eps、json、またはhtmlのいずれかである場合、それがファイルの形式になります。デフォルトでは、形式は `fn` の拡張子から推測されます。`scale` は画像のスケールを設定します。`width` と `height` は、ピクセル単位での寸法を設定します。デフォルトは `p.layout` から取得されるか、plotly によって提供されます。
