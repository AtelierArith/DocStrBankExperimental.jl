```
fit!(lds::LinearDynamicalSystem{S,O}, y::Matrix{T}; 
     max_iter::Int=1000, 
     tol::Real=1e-12, 
     ) where {T<:Real, S<:GaussianStateModel{T}, O<:GaussianObservationModel{T}}
```

線形動的システムを期待値最大化（EM）アルゴリズムを使用してフィットし、カルマン平滑化を行います。

# 引数

  * `lds::LinearDynamicalSystem{S,O}`: フィットする線形動的システム。
  * `y::Matrix{T}`: 観測データ、サイズ (obs*dim, T*steps)。

# キーワード引数

  * `max_iter::Int=1000`: EM反復の最大数。
  * `tol::Real=1e-12`: 対数尤度変化の収束許容範囲。

# 戻り値

  * `mls::Vector{T}`: 各反復の対数尤度値のベクトル。
