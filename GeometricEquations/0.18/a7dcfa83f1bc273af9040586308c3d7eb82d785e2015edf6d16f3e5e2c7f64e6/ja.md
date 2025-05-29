`IDAEProblem`: 暗黙の微分代数方程式問題

暗黙の微分代数初期値問題は次の形を取ります

$$
\begin{aligned}
\dot{q} (t) &= v(t) + u(t, q(t), v(t), p(t), \lambda(t)) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), p(t), \lambda(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) , \\
0 &= \phi (t, q(t), v(t), p(t)) ,
\end{aligned}
$$

力場 $f$、モーメントを定義する $ϑ$、射影 $u$ と $g$、代数制約 $\phi(t,q,v,p)=0$ があります。

いくつかの積分器は、代数制約 $\phi$ の時間微分である二次制約 $\psi$ も強制します。この場合、方程式の系は次のように修正されます

$$
\begin{aligned}
\dot{q} (t) &= v(t) + u(t, q(t), v(t), p(t), \lambda(t)) + \bar{u} (t, q(t), v(t), p(t), \mu(t)) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), p(t), \lambda(t)) + \bar{g} (t, q(t), v(t), p(t), \mu(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) , && \\
0 &= \phi (t, q(t), v(t), p(t)) , \\
0 &= \psi (t, q(t), v(t), p(t), \dot{q} (t), \dot{p} (t)) .
\end{aligned}
$$

動的変数 $(q,p)$ は初期条件 $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ を持ち、$\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取ります。代数変数 $(λ,μ)$ は初期条件 $(λ(t_{0}) = λ_{0}, μ(t_{0}) = μ_{0})$ を持ち、$\mathbb{R}^{m} \times \mathbb{R}^{m}$ の値を取ります。

### コンストラクタ

```julia
IDAEProblem(ϑ, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, ics; kwargs...)
IDAEProblem(ϑ, f, u, g, ϕ, ū, ḡ, ψ, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable = zero(q₀), μ₀::StateVariable = zero(λ₀); kwargs...)
IDAEProblem(ϑ, f, u, g, ϕ, tspan, tstep, ics; kwargs...)
IDAEProblem(ϑ, f, u, g, ϕ, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable = zero(q₀); kwargs...)
```

関数 `ϑ` はモーメントを計算し、`f` は力場を計算し、`u` と `g` は射影を計算し、`ϕ` は代数制約を提供します。関数 `ψ`、`ū` および `ḡ` はオプションであり、代数制約の時間微分である二次制約と対応する射影を提供します。

`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップであり、`ics` は `NamedTuple` で `q` と `p` のエントリを持ちます。初期条件 `q₀`、`p₀`、`λ₀` および `μ₀` は直接指定することもでき、`StateVariable` は `AbstractArray{<:Number}` です。関数 `ϑ`、`f`、`u`、`g`、`ϕ`、`ū`、`ḡ`、`ψ` のインターフェースについては [`IDAE`](@ref) を参照してください。

[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに対する標準のキーワード引数に加えて、`IDAEProblem` は初期推定値の計算のために関数 `v̄` と `f̄` を受け入れ、デフォルト値は `v̄ = _idae_default_v̄` および `f̄ = f` です。

### 関数定義

関数 `ϑ` と `f` は次のインターフェースを持たなければなりません

```julia
function ϑ(p, t, q, v, params)
    p[1] = ...
    p[2] = ...
    ...
end

function f(f, t, q, v, params)
    f[1] = ...
    f[2] = ...
    ...
end
```

ここで `t` は現在の時間、`q` は現在の解ベクトル、`v` は現在の速度であり、`f` と `p` は関数 $f$ と $ϑ$ を `t`、`q`、`v` で評価した結果を保持するベクトルです。関数 `g`、`v̄` および `f̄` は次のように指定されます

```julia
function u(u, t, q, v, p, λ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function g(g, t, q, v, p, λ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function v̄(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f̄(f, t, q, v, params)
    f[1] = ...
    f[2] = ...
    ...
end
```

いくつかの積分器は二次制約 $\psi$ を強制し、次の追加関数を必要とします

```
function ū(u, t, q, v, p, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ḡ(g, t, q, v, p, μ, params)
    g[1] = ...
    g[2] = ...
    ...
end

function ψ(ψ, t, q, v, p, q̇, ṗ, params)
    ψ[1] = ...
end
```
