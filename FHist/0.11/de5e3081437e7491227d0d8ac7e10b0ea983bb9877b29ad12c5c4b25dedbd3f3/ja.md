```
push!(h::Hist3D, valx::Real, valy::Real, wgt::Real=1)
atomic_push!(h::Hist3D, valx::Real, valy::Real, wgt::Real=1)
```

ヒストグラムに1つの値を追加します。`sumw2`（重みの二乗の合計）は、デフォルトの重み1で`wgt^2`を累積します。`atomic_push!`は、スレッドセーフな`push!`の遅いバージョンです。
