```
fit(DCCspec::Type{<:DCC{p, q, VS<:UnivariateVolatilitySpec}}, data::Matrix;
    method=:largescale,  dist=MultivariateStdNormal, meanspec=Intercept,
    algorithm=BFGS(), autodiff=:forward, kwargs...)
```

`DCCspec`によって指定されたDCCモデルを`data`にフィットさせます。`p`と`q`または`VS`が指定されていない場合、これらはそれぞれ1、1、および`GARCH{1, 1}`にデフォルト設定されます。

# キーワード引数:

  * `method`: `:largescale`または`twostep`のいずれか
  * `dist`: 誤差分布。
  * `meanspec`: 平均仕様、型として。
  * `algorithm, autodiff, kwargs, ...`: 最適化器に渡されます。

# 例: DCC{1, 1, GARCH{1, 1}}モデル:

```jldoctest
julia> fit(DCC, DOW29)

29次元DCC{1, 1} - GARCH{1, 1} - Intercept{Float64}仕様、T=2785。

DCCパラメータ、ラージスケール手法によって推定:
────────────────────
       β₁         α₁
────────────────────
  0.88762  0.0568001
────────────────────

標準誤差の計算は高コストです。これを表示するには、
`show(IOContext(stdout, :se=>true), <model>)`を使用してください。
```
