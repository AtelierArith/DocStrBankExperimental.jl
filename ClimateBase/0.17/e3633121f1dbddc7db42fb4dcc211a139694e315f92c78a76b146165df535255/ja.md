```
sinusoidal_continuation(T::ClimArray, fs = [1, 2]; Tmin = -Inf, Tmax = Inf)
```

空間時間フィールド `T` の欠損値を埋めるために、欠損していない値に対して正弦波をフィッティングし、フィッティングされた正弦波を欠損値に使用します。

周波数は年ごとに与えられます（周波数 2 は 1 年の 1/2 を意味します）。

`Tmin, Tmax` の制限は、結果をこの範囲にクランプするために使用されます（デフォルトの場合はクランプなし）。
