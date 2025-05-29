###### gattino コンテキストスタイリング

```julia
style!(con::AbstractContext, args ...) -> ::Nothing
```

`style!` は `Gattino` コンテキストで動作するように拡張されています。ウィンドウをスタイルするには `style!(con::AbstractContext, spairs::Pair{String, String} ...)` を使用し、レイヤーをスタイルするには `style!(con::AbstractContext, s::String, spairs::Pair{String, String} ...)` を使用します。これは通常のコンポーネントと同様です。

```julia
style!(con::AbstractContext, s::String, spairs::Pair{String, String} ...)
style!(con::AbstractContext, spairs::Pair{String, String} ...)
```

  * 参照: `animate!(::AbstractContext, ::String, ::ToolipsSVG.KeyFrames)`, `set!`, `Context`, `layers`

```example

```
