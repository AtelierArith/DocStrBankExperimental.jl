```
opening!(out, img, buffer; [dims], [r])
opening!(out, img, se, buffer)
```

入力画像 `img` と出力画像 `out` を持つ [`opening`](@ref) のインプレースバージョン。中間の侵食結果は `buffer` に格納されます。
