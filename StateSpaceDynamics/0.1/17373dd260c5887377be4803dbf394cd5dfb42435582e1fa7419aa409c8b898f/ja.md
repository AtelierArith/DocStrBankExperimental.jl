```
estep(lds::LinearDynamicalSystem{S,O}, y::Array{T,3}) where {T<:Real, S<:GaussianStateModel{T}, O<:AbstractObservationModel{T}}
```

EMアルゴリズムのEステップを線形動的システムに対して実行し、すべての入力をマルチトライアルとして扱います。

# 引数

  * `lds::LinearDynamicalSystem{S,O}`: 線形動的システム構造体
  * `y::Array{T,3}`: 観測データ、サイズ (obs*dim, T*steps, n*trials)   注意: シングルトライアルデータの場合、y[1:1, :, :]を使用してn*trials = 1の3D配列を作成します。

# 戻り値

  * `E_z::Array{T,3}`: 期待される潜在状態、サイズ (state*dim, state*dim, T*steps, n*trials)
  * `E_zz::Array{T,4}`: 期待されるz*t * z*t'、サイズ (state*dim, state*dim, T*steps, n*trials, state_dim)
  * `E_zz_prev::Array{T,4}`: 期待されるz*t * z*{t-1}'、サイズ (state*dim, state*dim, T*steps, n*trials, state_dim)
  * `x_smooth::Array{T,3}`: スムーズ化された状態推定、サイズ (state*dim, state*dim, T*steps, n*trials)
  * `p_smooth::Array{T,4}`: スムーズ化された状態共分散、サイズ (state*dim, state*dim, T*steps, n*trials, state_dim)
  * `ml::T`: すべてのトライアルにわたるデータの総周辺尤度（対数尤度）

# 注意

  * この関数は最初に`smooth`関数を使用してデータをスムーズ化し、その後十分な統計量を計算します。
  * すべての入力をマルチトライアルとして扱い、シングルトライアルはn_trials = 1の特別なケースです。
