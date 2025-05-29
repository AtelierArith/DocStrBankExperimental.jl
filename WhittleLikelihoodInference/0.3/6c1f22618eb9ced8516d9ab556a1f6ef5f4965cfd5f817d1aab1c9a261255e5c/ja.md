```
EI(model::TimeSeriesModel, n, Δ)
```

フーリエ周波数 `fftshift(fftfreq(n,2π/Δ))` で EI を計算します。

内部計算は2倍の解像度で値を提供しますが、この関数は希望する解像度で返します。
