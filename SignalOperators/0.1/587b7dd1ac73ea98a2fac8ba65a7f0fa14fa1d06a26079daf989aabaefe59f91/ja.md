```
bandpass(x,low,high;[order=5],[method=Butterworth(order)],[blocksize])
```

与えられたカットオフ周波数（`low` と `high`）で x にバンドパスフィルターを適用します。`blocksize` の詳細については [`filtersignal`](@ref) を参照してください。
