```
label(nmrdata)
label(nmrdata, dim)
label(nmrdimension)
```

`NMRData` 構造体または `NMRDimension` に関連付けられた短いラベルを返します。デフォルトでは、スペクトルの場合、これはタイトルファイルの最初の行から取得されます。周波数次元の場合、通常は `1H 化学シフト (ppm)` の形式の何かです。

[`label!`](@ref) も参照してください。
