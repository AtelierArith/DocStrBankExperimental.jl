`LODEProblem`: ラグランジュ常微分方程式問題

ラグランジュ系の方程式は、暗黙の常微分方程式の特別なケースであり、次の形式の暗黙の初期値問題です。

$$
\begin{aligned}
\dot{q} (t) &= v(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

運動量 $p$ と力場 $f$ は次のように与えられます。

$$
\begin{aligned}
p &= \frac{\partial L}{\partial v} , &
f &= \frac{\partial L}{\partial q} .
\end{aligned}
$$

これは、ラグランジュによって定義される暗黙の常微分方程式の特別なケースであり、動的変数 $(q,p)$ と代数変数 $v$ を持つ微分代数方程式の特別なケースでもあります。この代数変数は、制約 $p(t) = ϑ(t, q(t), v(t))$ が満たされるように決定されます。

多くの積分器は、この制約を強制するために投影ステップを実行します。この目的のために、システムは次のように拡張されます。

$$
\begin{aligned}
\dot{q} (t) &= v(t) + \lambda(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), \lambda(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

ここで、投影ステップを定義するベクトル場は通常次のように与えられます。

$$
\begin{aligned}
g(t, q(t), v(t), λ(t)) &= λ(t) \cdot \nabla ϑ(t, q(t), v(t)) .
\end{aligned}
$$

初期条件 $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ を持つ動的変数 $(q,p)$ は $T^{*} Q \simeq \mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取ります。初期条件 $λ(t_{0}) = λ_{0}$ を持つ代数変数 $λ$ は $\mathbb{R}^{m}$ の値を取ります。

### コンストラクタ

```julia
LODEProblem(ϑ, f, ω, l, tspan, tstep, ics; kwargs...)
LODEProblem(ϑ, f, ω, l, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::AlgebraicVariable; kwargs...)
LODEProblem(ϑ, f, ω, l, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray, λ₀::AbstractArray = zero(q₀); kwargs...)
LODEProblem(ϑ, f, g, ω, l, tspan, tstep, ics; kwargs...)
LODEProblem(ϑ, f, g, ω, l, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::AlgebraicVariable; kwargs...)
LODEProblem(ϑ, f, g, ω, l, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray, λ₀::AbstractArray = zero(q₀); kwargs...)
```

ここで `ϑ`、`f` および `g` はそれぞれ運動量とベクトル場を計算する関数であり、`ω` はシンプレクティック行列を決定し、`l` はラグランジュを返します。`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップです。`ics` は `NamedTuple` で、`q`、`p` および `λ` のエントリを持ちます。初期条件 `q₀`、`p₀` および `λ₀` は直接指定することもでき、`StateVariable` は `AbstractArray{<:Number}` であり、`λ₀` は省略することもできます。関数 `ϑ`、`f`、`g`、`ω` および `l` のインターフェースについては [`LODE`](@ref) を参照してください。

[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに対する標準のキーワード引数に加えて、`LODEProblem` は初期推定値の計算のために関数 `v̄` と `f̄` を受け入れ、デフォルト値は `v̄ = _lode_default_v̄` および `f̄ = f` です。
