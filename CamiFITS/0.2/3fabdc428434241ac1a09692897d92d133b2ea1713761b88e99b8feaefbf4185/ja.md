```
FITS_header
```

[`FITS_HDU`](@ref)のヘッダー情報を保持するオブジェクトです。

フィールドは次のとおりです：

  * `.card`: `cards`の配列（`::Vector{FITS_card}`）
  * `.map`: 辞書 `keyword => recordindex`（`::Dict{String, Int}`）
  * `.size`: バイト単位の長さ（`::Int`）
