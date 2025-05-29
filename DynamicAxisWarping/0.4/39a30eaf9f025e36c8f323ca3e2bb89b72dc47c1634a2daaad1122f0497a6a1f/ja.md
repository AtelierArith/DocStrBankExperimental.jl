```
soft_dtw_cost(args...; γ = 1, kwargs...)
```

ソフトDTWを実行します。これはDTWの微分可能なバージョンです。この関数が返す「距離」は真の距離からかなり離れており、負の値になることもあります。`γ`の値が小さいほど、距離は標準のDTW距離に近くなります。

最初の引数に対して微分を行うには、次のようにします。

```julia
using ReverseDiff
da = ReverseDiff.gradient(a->soft_dtw_cost(a,b), a)
```

参考文献: "Soft-DTW: a Differentiable Loss Function for Time-Series" https://arxiv.org/pdf/1703.01541.pdf

# 引数:

  * `args`: [`dtw`](@ref)と同じ
  * `γ`: スムージング係数。小さい値はスムージングが少なく、[`dtw_cost`](@ref)に近い結果を意味します
  * `kwargs`: [`dtw`](@ref)と同じ

```
