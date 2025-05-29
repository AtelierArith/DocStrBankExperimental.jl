`PDAEProblem`: 分割微分代数方程問題

分割微分代数方程は次の形を持ちます

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) + u(t, q(t), p(t), \lambda(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) + g(t, q(t), p(t), \lambda(t)) , \\
0 &= \phi (t, q(t), p(t)) ,
\end{aligned}
$$

ベクトル場 $v$ と $f$、射影 $u$ と $g$、代数制約 $\phi=0$ を持っています。

いくつかの積分器は、代数制約 $\phi$ の時間微分である二次制約 $\psi$ も強制します。この場合、方程式の系は次のように修正されます

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) + u(t, q(t), p(t), \lambda(t)) + \bar{u} (t, q(t), p(t), \mu(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) + g(t, q(t), p(t), \lambda(t)) + \bar{g} (t, q(t), p(t), \mu(t)) , \\
0 &= \phi (t, q(t), p(t)) , \\
0 &= \psi (t, q(t), p(t), \dot{q} (t), \dot{p} (t)) .
\end{aligned}
$$

動的変数 $(q,p)$ は初期条件 $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ を持ち、値は $\mathbb{R}^{d} \times \mathbb{R}^{d}$ に取ります。代数変数 $(λ,μ)$ は初期条件 $(λ(t_{0}) = λ_{0}, μ(t_{0}) = μ_{0})$ を持ち、値は $\mathbb{R}^{m} \times \mathbb{R}^{m}$ に取ります。

### コンストラクタ

```julia
PDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, ics::NamedTuple; kwargs...)
PDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable, μ₀::StateVariable = zero(λ₀); kwargs...)
PDAEProblem(v, f, u, g, ϕ, tspan, tstep, ics::NamedTuple; kwargs...)
PDAEProblem(v, f, u, g, ϕ, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable; kwargs...)
```

関数 `v` と `f` はベクトル場を計算し、`u` と `g` は射影を計算し、`ϕ` は代数制約を提供します。関数 `ψ`、`ū` および `ḡ` はオプションで、二次制約と対応する射影を提供します。

`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップであり、`ics` は `NamedTuple` で、エントリ `q`、`p`、`λ` および `μ` を持ちます。初期条件 `q₀`、`p₀`、`λ₀` および `μ₀` も直接指定でき、`StateVariable` は `AbstractArray{<:Number}` です。関数 `v`、`f`、`u`、`g`、`ϕ`、`ū`、`ḡ`、`ψ` のインターフェースについては [`PDAE`](@ref) を参照してください。

[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに対する標準のキーワード引数に加えて、`PDAEProblem` はベクトル場の初期推測を計算するための関数 `v̄` と `f̄` を受け入れ、デフォルト値は `v̄ = v` および `f̄ = f` です。

### 関数定義

関数 `v`、`f`、`u`、`g` および `ϕ` は次のインターフェースを持たなければなりません

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f(g, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function u(u, t, q, p, λ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function g(g, t, q, p, λ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function ϕ(ϕ, t, q, p, params)
    ϕ[1] = ...
end
```

ここで `t` は現在の時間、`q`、`p` および `λ` は現在の解ベクトル、`v`、`f`、`u` および `g` はベクトル場 $v$ と $f$ の評価結果を保持するベクトル、射影 $u$ と $g$、そして `ϕ` は `t`、`q`、`p` および `λ` で評価された代数制約 $\phi$ を保持します。

いくつかの積分器は二次制約 $\psi$ も強制し、次の追加関数を必要とします

```
function ū(u, t, q, p, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ḡ(g, t, q, p, μ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function ψ(ψ, t, q, p, v, f, params)
    ψ[1] = ...
end
```

上記の関数定義を使用して `PDAEProblem` を作成することができます

```julia
tspan = (0.0, 1.0)
tstep = 0.1
q₀ = [1., 1.]
p₀ = [1., 0.]
λ₀ = [0.]
μ₀ = [0.]

prob = PDAEProblem(v, f, u, g, ϕ, tspan, tstep, q₀, p₀, λ₀)
```

または

```julia
prob = PDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, q₀, p₀, λ₀, μ₀)
```
