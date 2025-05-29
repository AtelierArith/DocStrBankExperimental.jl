```
apply(f:: Function, c1:: Curve; axis:: Symbol = :xy, kwargs...)
```

If ˋaxisˋ is ˋ:xyˋ (default): applies a 2-argument function ˋf(x,y)=zˋ to each entry of the Curve.

If ˋaxisˋ is ˋ:xˋ or ˋ:yˋ: applies a 1-argument function ˋf(x)=zˋ to a single axis of the Curve.

The output Curve is constructed using default settings, alternative settings can be passed to the Curve constructor using the ˋkwargs...ˋ
