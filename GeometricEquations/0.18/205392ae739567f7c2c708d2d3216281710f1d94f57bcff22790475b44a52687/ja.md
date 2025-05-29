`IODEEnsemble`: 暗黙の常微分方程式アンサンブル

暗黙の常微分方程式は、次の形の初期値問題です。

$$
\begin{aligned}
\dot{q} (t) &= v(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

ここで、力場 $f$ と運動量 $p$ が定義されています。これは、動的変数 $(q,p)$ と代数変数 $v$ を持つ微分代数方程式の特別なケースであり、制約 $p(t) = ϑ(t, q(t), v(t))$ が満たされるように決定されます。

多くの積分器は、この制約を強制するために投影ステップを実行します。この目的のために、システムは次のように拡張されます。

$$
\begin{aligned}
\dot{q} (t) &= v(t) + λ(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), λ(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

ここで、投影ステップを定義するベクトル場は通常次のように与えられます。

$$
\begin{aligned}
g(t, q(t), v(t), λ(t)) &= λ(t) \cdot \nabla ϑ(t, q(t), v(t)) .
\end{aligned}
$$

動的変数 $(q,p)$ は $\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取ります。代数変数 $λ$ は $\mathbb{R}^{m}$ の値を取ります。

### コンストラクタ

```julia
IODEEnsemble(ϑ, f, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
IODEEnsemble(ϑ, f, tspan, tstep, q₀::AbstractVector{<: StateVariable}, p₀::AbstractVector{<: StateVariable}, λ₀::AbstractVector{<: AlgebraicVariable}; kwargs...)
IODEEnsemble(ϑ, f, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, p₀::AbstractVector{<: AbstractArray}, λ₀::AbstractVector{<: AbstractArray}; kwargs...)
IODEEnsemble(ϑ, f, g, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
IODEEnsemble(ϑ, f, g, tspan, tstep, q₀::AbstractVector{<: StateVariable}, p₀::AbstractVector{<: StateVariable}, λ₀::AbstractVector{<: AlgebraicVariable}; kwargs...)
IODEEnsemble(ϑ, f, g, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, p₀::AbstractVector{<: AbstractArray}, λ₀::AbstractVector{<: AbstractArray}; kwargs...)
```

関数 `ϑ`、`f` および `g` は、それぞれ運動量とベクトル場を計算します。

`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップです。また、`ics` は `q`、`p` および `λ` のエントリを持つ `NamedTuple` です。`ics` は `NamedTuple` のエントリ `q`、`p` および `λ` を持つ `AbstractVector` です。初期条件 `q₀`、`p₀` および `λ₀` も指定でき、それぞれ `StateVariable` または `AbstractArray{<:Number}` の `AbstractVector` として指定されます。関数 `ϑ`、`f` および `g` のインターフェースについては、[`IODE`](@ref) を参照してください。

[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに対する標準のキーワード引数に加えて、`IODEEnsemble` はベクトル場の初期推定を計算するための関数 `v̄` と `f̄` を受け入れ、デフォルト値は `v̄ = _iode_default_v̄` および `f̄ = f` です。

可能なキーワード引数については、[`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) のドキュメントを参照してください。
