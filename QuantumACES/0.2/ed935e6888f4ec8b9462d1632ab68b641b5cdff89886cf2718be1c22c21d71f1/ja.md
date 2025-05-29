```
calc_merit(d::Design; warning::Bool = true)
calc_merit(d_rand::RandDesign; warning::Bool = true)
```

デザイン `d` またはランダム化デザイン `d_rand` に対応する [`Merit`](@ref) オブジェクトを返し、デザインに完全な共分散行列データがない場合は警告を表示し、`warning` が `true` の場合に限ります。
