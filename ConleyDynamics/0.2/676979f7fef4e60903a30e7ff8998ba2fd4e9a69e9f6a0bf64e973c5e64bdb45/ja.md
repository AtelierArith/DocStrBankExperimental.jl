```
lefschetz_skeleton(lc::LefschetzComplex, subcomp::Vector{String}, skdim::Int)
```

Lefschetz複体部分集合の`skdim`次元スケルトンを計算します。

計算されたスケルトンは、`subcomp`によって与えられた部分複体の閉包に対するものです。
