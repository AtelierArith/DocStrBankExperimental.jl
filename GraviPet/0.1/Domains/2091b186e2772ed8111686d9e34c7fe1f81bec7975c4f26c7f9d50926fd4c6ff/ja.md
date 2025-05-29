```
expanded(dom::Domain, delta)::Domain
expanded(dom::Domain, delta_lo, delta_hi)::Domain
```

ドメイン `dom` を拡張します。下限および上限のドメイン境界は、それぞれ `delta` または `delta_lo` と `delta_hi` によって移動されます。正のデルタはドメインを拡大し、負の値はそれを縮小します。ドメインは空であってはなりません。

`expanded(dom, delta)` は `expanded(dom, delta, delta)` と同等です。

詳細は [`shifted`](@ref) を参照してください。
