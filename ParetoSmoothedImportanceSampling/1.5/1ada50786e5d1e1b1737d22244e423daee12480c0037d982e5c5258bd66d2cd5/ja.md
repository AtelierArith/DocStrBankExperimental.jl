```
waic(ll::AbstractArray{<:Real}; pointwise=false, log_lik="log_lik, kwargs...)
```

広く適用可能な情報基準 (WAIC) を計算します。

# 引数

  * `loglik::AbstractArray`   : 事後対数尤度のベクトル
  * `pointwise::Bool`         : WAICをポイントごとに計算し、ベクトルを返す

# 戻り値

  * `res::NamedTuple`: (WAIC=waics, lppd=lpd, penalty=pD, std_err=se) ここで

    WAIC                    : ポイントごとのwaic値の合計（またはポイントごとのベクトル）   lppd                    : ポイントごとの予測密度の対数   penalty                 : ペナルティ項（「過剰適合ペナルティ」）   std_err                 : ポイントごとのwaic値の標準誤差

```
