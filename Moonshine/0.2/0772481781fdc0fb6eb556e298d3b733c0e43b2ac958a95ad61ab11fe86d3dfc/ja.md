```
build!(rng, genealogy; kwargs...)
```

系譜を構築します。

# メソッド

```julia
build!(rng, arg; winwidth, buffer, noprogress)
```

[`packages/Moonshine/7JVTP/src/Arg/Recombination.jl:681`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Recombination.jl) で定義されています。

```julia
build!(rng, tree; Dist, bias0, threshold_prop)
```

[`packages/Moonshine/7JVTP/src/Tree.jl:243`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Tree.jl) で定義されています。

# 引数

  * `winwidth` (`∞`): 考慮する位置のウィンドウの幅
  * `noprogress` (`false`): 進行状況バーを非表示にする
  * `Dist` (`Hamming{Int}()`): 合流確率を計算するために使用される距離
  * `bias0` (`10`): 距離の倍率: 高い値は類似のハプロタイプ間の合流イベントを優先します
  * `threshold_prop` (`1`): サンプリング時に考慮するイベントの割合
