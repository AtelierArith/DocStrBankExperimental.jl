```
betaU_SW(temperature::T_num, lambda_range::T_num, k::T_num) where {T_num<:AbstractFloat}
```

補助関数で、引力部分の平方井戸（SW）ポテンシャルのフーリエ変換を計算し、β = 1/(k*B T*abs)で乗算します。結果はβ * u*attr*SW_tilde(k)です。

# 引数

  * `temperature::T_num`: 無次元温度（通常はk*B * T*abs / ε、ここでεは井戸の深さ）。
  * `lambda_range::T_num`: 硬球直径σに関する平方井戸の範囲（すなわち、λ*σ）。
  * `k::T_num`: 無次元波ベクトル（k = q*σ）。

# 戻り値

  * `T_num`: β * u*attr*SW_tilde(k)の値。
