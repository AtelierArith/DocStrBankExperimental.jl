```
maxpixel(hss::HyperSpectrum, filt=ci->true)
maxpixel(hss::HyperSpectrum, cis::CartesianIndices, filt=ci->true)
maxpixel(hss::HyperSpectrum, mask::BitArray)
minpixel(hss::HyperSpectrum, filt=ci->true)
minpixel(hss::HyperSpectrum, cis::CartesianIndices, filt=ci->true)
minpixel(hss::HyperSpectrum, mask::BitArray)
```

全体のハイパースペクトルまたは矩形のサブリージョンに対して、ブライトの最大ピクセル派生信号を計算します。
