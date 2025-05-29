`ODEEnsemble`: 常微分方程のアンサンブル

常微分方程式は、次の形の初期値問題を定義します。

$$
\dot{q} (t) = v(t, q(t)) ,
$$

ベクトル場 $v$ を用いて。

動的変数 $q$ は $\mathbb{R}^{d}$ の値を取ります。

### コンストラクタ

```julia
ODEEnsemble(v, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
ODEEnsemble(v, tspan, tstep, q₀::AbstractVector{<: StateVariable}; kwargs...)
ODEEnsemble(v, tspan, tstep, q₀::AbstractVector{<: AbstractArray}; kwargs...)
```

ここで `v` はベクトル場を計算する関数であり、`tspan` は問題を解くための時間区間 `(t₀,t₁)` で、`tstep` はシミュレーションで使用される時間ステップ、`ics` は `StateVariable` 型のエントリ `q` を持つ `NamedTuple` の `AbstractVector` です。初期条件 `q₀` は `StateVariable` または `AbstractArray{<:Number}` の `AbstractVector` としても指定できます。関数 `v` のインターフェースについては [`ODE`](@ref) を参照してください。

可能なキーワード引数については、[`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) サブタイプのドキュメントを参照してください。
