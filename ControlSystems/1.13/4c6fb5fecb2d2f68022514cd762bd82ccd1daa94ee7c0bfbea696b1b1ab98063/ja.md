```
lsim(sys::HammersteinWienerSystem, u, t::AbstractArray{<:Real}; x0=fill(0.0, nstates(sys)), alg=Tsit5(), abstol=1e-6, reltol=1e-6, kwargs...)
```

システム `sys` を、入力信号 `u` を使用して、初期状態 `x0` で、時間 `t` にわたってシミュレートします。

# 引数:

  * `t`: 等間隔の時間サンプルを持つ `AbstractVector` でなければなりません（`t[i] - t[i-1]` が一定）
  * `u`: 時間 `t` における制御信号 `uₜ` を決定する関数で、以下のいずれかの形式を取ることができます:   定数 `Number` または `Vector` で、`uₜ .= u` と解釈されるか、   関数 `uₜ .= u(x, t)`、または   インプレース関数 `u(uₜ, x, t)`。 （わずかに効率的）
  * `alg, abstol, reltol` および `kwargs...`: `OrdinaryDiffEq.solve` に送られます。

[`SimResult`](@ref) のインスタンスを返します。
