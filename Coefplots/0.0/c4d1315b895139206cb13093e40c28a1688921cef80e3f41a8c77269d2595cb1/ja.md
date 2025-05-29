```
Note <: PGFPlotsX.TikzElement
```

# コンストラクタ

```julia
Note(;content=missing, anchor=missing ,at=missing, align=missing, captionstyle=missing)
```

# キーワード引数

  * `content::Union{String, Missing}` はノートの内容です。
  * `anchor::Union{Symbol, String, Missing}` はアライメントに使用されるノートボックスのアンカーを指定します。典型的なものは `"north west"` です。
  * `at::Any` はアンカーが従うべき軸フレーム内の位置を指定します。典型的なものは `(1, 0)` で、これはアンカーが軸フレームの南東隅に固定されることを意味します。
  * `align::Union{Symbol, String, Missing}` はノートのアライメント方法を指定します。`"left"`、`"right"`、または `"center"` である可能性があります。
  * `captionstyle::Union{captionstyle, Missing}` はノートのキャプションスタイルです。
