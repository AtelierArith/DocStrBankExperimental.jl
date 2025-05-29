AffineDiffEqOperator{T} <: AbstractDiffEqOperator{T}

`Ex: (A₁(t) + ... + Aₙ(t))*u + B₁(t) + ... + Bₘ(t)`

AffineDiffEqOperator{T}(As,Bs,du_cache=nothing)

2つのタプルを受け取り、分割アフィン微分方程式を処理します。

1. update_coefficients! は、コンポーネントオペレーターの係数を更新することによって機能します。
2. 関数呼び出し L(u, p, t) および L(du, u, p, t) は、この形式で解釈されるフォールバックです。これにより、非線形ODEソルバーで直接機能することができます。
3. f(du, u, p, t) は、du_cacheが与えられた場合にのみ許可されます。
4. B(t) は Union{Number,AbstractArray} であり、その場合は定数です。そうでない場合は、関数 v=B(t) および B(v,t) として解釈されます。

ソルバーは integrator.f からこのオペレーターを確認し、As と Bs の内部をチェックすることで解釈できます。たとえば、isconstant(As[1]) などをチェックできます。
