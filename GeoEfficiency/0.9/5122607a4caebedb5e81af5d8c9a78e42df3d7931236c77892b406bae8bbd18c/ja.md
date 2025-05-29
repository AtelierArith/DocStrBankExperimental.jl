```
calc(detector::Detector = Detector(), aSource::Tuple{Point, Float64, Float64,} = source())
```

検出器 `detector` の `aSource` タプルで説明されるソースの `幾何学的効率` を計算して `console` に表示します。

**`Throw`**  不適切なソース位置の場合は `inValidGeometry` を投げます。

**参照:** [`geoEff(::Detector, ::Tuple{Point, Float64, Float64})`](@ref)

!!! note
    ソースの説明 `aSource` のみ、またはソースの説明と検出器 `detect` の両方が欠けている場合、メソッドは `console` を通じてユーザーに欠けているデータを補完するよう促します。

