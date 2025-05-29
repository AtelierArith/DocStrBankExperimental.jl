```
bothat!(out, img, buffer; [dims], [r])
bothat!(out, img, se, buffer)
```

入力画像 `img` と出力画像 `out` を持つ [`bothat`](@ref) のインプレースバージョン。中間の膨張結果は `buffer` に格納されます。
