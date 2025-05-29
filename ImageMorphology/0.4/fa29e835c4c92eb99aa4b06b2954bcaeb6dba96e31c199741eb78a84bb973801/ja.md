```
mlaplacian!(out, img, buffer; [dims], [r])
mlaplacian!(out, img, se, buffer)
```

入力画像 `img` と出力画像 `out` を持つ [`mlaplacian`](@ref) のインプレースバージョンです。中間の侵食結果は `buffer` に保存されます。
