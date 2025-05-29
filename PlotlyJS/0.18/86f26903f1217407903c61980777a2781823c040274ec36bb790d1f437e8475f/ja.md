```
savefig(
    io::IO,
    p::Plot;
    width::Union{Nothing,Int}=nothing,
    height::Union{Nothing,Int}=nothing,
    scale::Union{Nothing,Real}=nothing,
    format::String="png"
)
```

プロット `p` を io ストリーム `io` に保存します。キーワード引数 `format` は、図に書き込まれるデータのタイプを決定し、png、jpeg、webp、svg、pdf、eps、json、または html のいずれかでなければなりません。`scale` は画像のスケールを設定します。`width` と `height` は、ピクセル単位での寸法を設定します。デフォルトは `p.layout` から取得されるか、plotly によって提供されます。
