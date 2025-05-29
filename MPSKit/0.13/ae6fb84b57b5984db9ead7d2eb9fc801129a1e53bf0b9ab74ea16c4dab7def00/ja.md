```
excitations(H, algorithm::QuasiparticleAnsatz, momentum::Union{Number, Vector{<:Number}},
            left_ψ::InfiniteMPS, [left_environment],
            [right_ψ::InfiniteMPS], [right_environment];
            kwargs...)
```

無限の準粒子状態を作成し、最適化します。

# 引数

  * `H::AbstractMPO`: 励起を見つけるための演算子
  * `algorithm::QuasiparticleAnsatz`: 最適化アルゴリズム
  * `momentum::Union{Number, Vector{<:Number}}`: 運動量または運動量のリスト
  * `left_ψ::InfiniteMPS`: 左側の基底状態
  * `[left_environment]`: 左側の基底状態環境
  * `[right_ψ::InfiniteMPS]`: 右側の基底状態
  * `[right_environment]`: 右側の基底状態環境

# キーワード

  * `num::Int`: 計算する励起状態の数
  * `solver`: 準粒子環境の線形ソルバーのアルゴリズム
  * `sector=one(sectortype(left_ψ))`: 準粒子状態の電荷
  * `parallel=true`: 異なる運動量に対してマルチスレッドを有効にする
