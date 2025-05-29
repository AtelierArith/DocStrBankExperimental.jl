```
linescan(hss::HyperSpectrum{T,2,3}, ci1::CartesianIndex{2}, ci2::CartesianIndex{2}, width::Int=1)
```

`hss` から `ci1` から `ci2` までのラインに沿ってピクセルを抽出し、1D HyperSpectrum として返します。`width` 引数は、主軸に垂直なラインに沿ってラインスキャンを統合します。2D SpectrumImages のみで機能し、`width` の奇数値に対してのみ有効です。アルゴリズムは時折ピクセルを二重にカウントしますが、各垂直の長さは `width` に保たれます。`AxisArrays.axes(...)` のスケーリングが維持されるため、ラインスキャンの長さは元のマップの長さと比較できます。
