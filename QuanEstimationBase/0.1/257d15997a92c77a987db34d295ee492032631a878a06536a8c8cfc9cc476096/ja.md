```
PSO(;max_episode::Union{T,Vector{T}} where {T<:Int}=[1000, 100], p_num::Number=10, ini_particle=nothing, c0::Number=1.0, c1::Number=2.0, c2::Number=2.0, seed::Number=1234)
```

最適化アルゴリズム: PSO。

  * `max_episode`: エピソードの数で、整数と2つの要素を持つ配列の両方を受け入れます。
  * `p_num`: 粒子の数。
  * `ini_particle`: 最適化変数の初期推定値。
  * `c0`: 収束を助ける減衰係数で、慣性重みとも呼ばれます。
  * `c1`: 粒子をその最良の以前の位置に引き寄せる利用重みで、認知学習係数とも呼ばれます。
  * `c2`: 粒子を近隣の最良の位置に引き寄せる利用重みで、社会的学習係数とも呼ばれます。
