```
DetectorHit = NamedTuple{(:evtno, :detno, :thit, :edep, :pos), ...)
```

検出器における局所的なエネルギー沈着の表現です。

コンパクトなメモリレイアウトを持つ `DetectorHit` の配列には [`DetectorHitEvents`](@ref) を使用してください。
