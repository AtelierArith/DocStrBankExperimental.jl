`IODEProblem`: 暗黙の常微分方程式問題

暗黙の常微分方程式は、次の形式の初期値問題です。

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

初期条件 $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ を持つ動的変数 $(q,p)$ は $\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取ります。初期条件 $v(t_{0}) = v_{0}$ を持つ代数変数 $v$ は $\mathbb{R}^{d}$ の値を取ります。

### コンストラクタ

```julia
IODEProblem(ϑ, f, tspan, tstep, ics; kwargs...)
IODEProblem(ϑ, f, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::AlgebraicVariable; kwargs...)
IODEProblem(ϑ, f, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray, λ₀::AbstractArray = zero(q₀); kwargs...)
IODEProblem(ϑ, f, g, tspan, tstep, ics; kwargs...)
IODEProblem(ϑ, f, g, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::AlgebraicVariable; kwargs...)
IODEProblem(ϑ, f, g, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray, λ₀::AbstractArray = zero(q₀); kwargs...)
```

関数 `ϑ`、`f` および `g` は、それぞれ運動量とベクトル場を計算します。

`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップです。また、`ics` は `NamedTuple` で、`q`、`p` および `λ` のエントリを持ちます。初期条件 `q₀` と `p₀` は、`StateVariable` が `AbstractArray{<:Number}` である場合、直接指定することもできます。関数 `ϑ`、`f` および `g` のインターフェースについては、[`IODE`](@ref) を参照してください。

[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに対する標準のキーワード引数に加えて、`IODEProblem` は、デフォルト値 `v̄ = _iode_default_v̄` および `f̄ = f` を持つベクトル場の初期推定値を計算するための関数 `v̄` と `f̄` を受け入れます。

初期条件は `(q,p)` に対して指定する必要があります。代わりに初期条件が `(q,v)` のみで利用可能な場合、関数 `ϑ` を呼び出して対応する初期値の `p` を計算することができます。
