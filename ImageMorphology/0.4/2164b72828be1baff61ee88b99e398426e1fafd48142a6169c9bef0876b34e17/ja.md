```
mgradient!(out, img, buffer; [dims], [r], [mode])
mgradient!(out, img, se, buffer; [mode])
```

入力画像 `img` と出力画像 `out` を持つ [`mgradient`](@ref) のインプレースバージョンです。

`:beucher` モードには `buffer` 配列が必要です。`:internal` および `:external` モードでは、`buffer` は必要なく、`nothing` にすることができます。
