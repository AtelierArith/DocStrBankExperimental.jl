```
kpm_coefs!(
    coefs::AbstractVector{T}, func::Function, bounds,
    buf::AbstractVector{T} = zeros(T, 2*length(coefs)),
    r2rplan = FFTW.plan_r2r!(buf, FFTW.REDFT10)
) where {T<:AbstractFloat}
```

関数 `func` の区間 `(bounds[1], bounds[2])` における次数 `M` のチェビシェフ多項式展開係数をベクトル `coefs` に計算して記録します。`buf` の長さは、チェビシェフ-ガウス数値積分を行う際に `func` が評価される区間上の等間隔の点の数を表します。
