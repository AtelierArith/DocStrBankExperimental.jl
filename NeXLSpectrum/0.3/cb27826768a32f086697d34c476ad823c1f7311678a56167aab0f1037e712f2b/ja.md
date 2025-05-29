```
indexofmaxpixel(hss::HyperSpectrum, ch::Int) # チャンネル `ch` で
indexofmaxpixel(hss::HyperSpectrum) # すべてのチャンネル
indexofmaxpixel(hss::HyperSpectrum, ch::Int, cis::CartesianIndices)
indexofmaxpixel(hss::HyperSpectrum, cis::CartesianIndices)
```

データ[ch] またはデータ[:] 内の 'cis' または全空間次元で最大値を生成するインデックスを見つけます。
