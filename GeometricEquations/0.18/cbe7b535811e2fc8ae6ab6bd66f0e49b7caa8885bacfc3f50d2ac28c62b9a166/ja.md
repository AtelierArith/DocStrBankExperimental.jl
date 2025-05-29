`SODEEnsemble`: 分割常微分方程アンサンブル

初期値問題を定義します

$$
\dot{q} (t) = v(t, q(t)) , \qquad q(t_{0}) = q_{0} ,
$$

ベクトル場 $v$、初期条件 $q_{0}$、および解 $q$ は $\mathbb{R}^{d}$ の値を取ります。ここで、ベクトル場 $v$ はベクトル場の和として与えられます

$$
v (t) = v_1 (t) + ... + v_r (t) .
$$

動的変数 $q$ は $\mathbb{R}^{d}$ の値を取ります。

### コンストラクタ

```julia
SODEEnsemble(v, q, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
SODEEnsemble(v, q, tspan, tstep, q₀::AbstractVector{<: StateVariable}; kwargs...)
SODEEnsemble(v, q, tspan, tstep, q₀::AbstractVector{<: AbstractArray}; kwargs...)
SODEEnsemble(v, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
SODEEnsemble(v, tspan, tstep, q₀::AbstractVector{<: StateVariable}; kwargs...)
SODEEnsemble(v, tspan, tstep, q₀::AbstractVector{<: AbstractArray}; kwargs...)
```

ここで `v` は各サブステップのベクトル場を計算する関数のタプル、`q` は各サブステップの解を計算する関数のオプションのタプル、`tspan` は問題を解くための時間区間 `(t₀,t₁)`、`tstep` はシミュレーションで使用する時間ステップ、`ics` は `NamedTuple` のエントリ `q` が `StateVariable` 型である `AbstractVector` です。初期条件 `q₀` は `StateVariable` または `AbstractArray{<:Number}` の `AbstractVector` としても指定できます。関数 `v` と `q` のインターフェースについては [`SODE`](@ref) を参照してください。

可能なキーワード引数については、[`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) のサブタイプに関するドキュメントを参照してください。
