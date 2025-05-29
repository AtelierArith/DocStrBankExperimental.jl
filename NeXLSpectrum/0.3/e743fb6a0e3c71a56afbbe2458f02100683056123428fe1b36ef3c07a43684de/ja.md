```
region(hss::HyperSpectrum{T, N}, ranges::AbstractRange...)::HyperSpectrum where {T<:Real,N}
```

`hss` ハイパースペクトル内のピクセルの範囲を表すハイパースペクトルのビューを作成します。データやプロパティをコピーしないため、領域への変更は `hss` にも反映されます。
