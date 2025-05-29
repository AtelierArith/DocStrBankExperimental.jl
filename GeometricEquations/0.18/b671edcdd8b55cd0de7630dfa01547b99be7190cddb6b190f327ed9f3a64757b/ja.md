`HDAEProblem`: ハミルトン微分代数方程式

ハミルトン微分代数方程式は、ディラック制約に従った標準的なハミルトン系の方程式である初期値問題です。

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) + u(t, q(t), p(t), \lambda(t)) + \bar{u} (t, q(t), p(t), \mu(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) + g(t, q(t), p(t), \lambda(t)) + \bar{g} (t, q(t), p(t), \mu(t)) , \\
0 &= \phi (t, q(t), p(t)) , \\
0 &= \psi (t, q(t), p(t), \dot{q}(t), \dot{p}(t)) ,
\end{aligned}
$$

ベクトル場 $v$, $u$, $\bar{u}$ と $f$, $g$, $\bar{g}$、主制約 $\phi(q,p)=0$ および副制約 $\psi(q,p,\dot{q},\dot{p})=0$ があります。

動的変数 $(q,p)$ は初期条件 $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ を持ち、$\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取ります。代数変数 $(λ,μ)$ は初期条件 $(λ(t_{0}) = λ_{0}, μ(t_{0}) = μ_{0})$ を持ち、$\mathbb{R}^{m} \times \mathbb{R}^{m}$ の値を取ります。

### コンストラクタ

```julia
HDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, h, tspan, tstep, ics::NamedTuple; kwargs...)
HDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, h, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable, μ₀::StateVariable = zero(λ₀); kwargs...)
HDAEProblem(v, f, u, g, ϕ, h, tspan, tstep, ics::NamedTuple; kwargs...)
HDAEProblem(v, f, u, g, ϕ, h, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable; kwargs...)
```

関数 `v` と `f` はベクトル場を計算し、`u` と `g` は射影を計算し、`ϕ` は代数制約を提供し、`h` はハミルトニアンを提供します。関数 `ψ`, `ū` および `ḡ` はオプションであり、副制約、すなわち代数制約の時間微分と対応する射影を提供します。

`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップであり、`ics` は `NamedTuple` で、エントリ `q`, `p`, `λ` および `μ` を持ちます。初期条件 `q₀`, `p₀`, `λ₀` および `μ₀` も直接指定でき、`StateVariable` は `AbstractArray{<:Number}` です。関数 `v`, `f`, `u`, `g`, `ϕ`, `ū`, `ḡ`, `ψ`, および `h` のインターフェースについては [`HDAE`](@ref) を参照してください。

[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに対する標準的なキーワード引数に加えて、`HDAEProblem` はベクトル場の初期推定を計算するための関数 `v̄` と `f̄` を受け入れ、デフォルト値は `v̄ = v` および `f̄ = f` です。

### 関数定義

関数 `v`, `f`, `u`, `g`, `ϕ` および `h` は次のインターフェースを持たなければなりません。

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

function h(t, q, p, params)
    ...
end
```

ここで `t` は現在の時間、`q`, `p`, `λ` および `μ` は現在の解ベクトル、`v`, `f`, `u` および `g` はベクトル場 $v$ と $f$ の評価結果を保持するベクトル、主制約 $u$ と $g$ の射影、`ϕ` は代数制約 $\phi$ を保持し、`h` はシステムのハミルトニアンを返します。すべて `t`, `q`, `p` および `λ` で評価されます。

一部の積分器は副制約 $\psi$ を強制し、次の追加関数を必要とします。

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

上記の関数定義を使用して `HDAEProblem` を作成することができます。

```julia
tspan = (0.0, 1.0)
tstep = 0.1
q₀ = [1., 1.]
p₀ = [1., 0.]
λ₀ = [0.]
μ₀ = [0.]

prob = HDAEProblem(v, f, u, g, ϕ, h, tspan, tstep, q₀, p₀, λ₀)
```

または

```julia
prob = HDAEProblem(v, f, u, g, ϕ, ū, ḡ, ψ, h, tspan, tstep, q₀, p₀, λ₀, μ₀)
```
