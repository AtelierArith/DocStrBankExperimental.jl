```
mw_VAR!(out::Array{tp, N}, datacube0mean::Array{tp,N}, windowsize::Int = 10) where {tp,N}
```

`mw_VAR()`の変更可能なバージョンです。入力データ`datacube0mean`の平均は0でなければなりません。`out`を適切に初期化してください：`out = datacube0mean`は誤った結果をもたらします。
