`LDAEProblem`: ラグランジュ微分代数方程式問題

暗黙の初期値問題の特別なケースは、次の形式のラグランジュ微分代数方程式です。

$$
\begin{aligned}
\dot{q} (t) &= v(t) + u(t, q(t), v(t), p(t), \lambda(t)) + \bar{u} (t, q(t), v(t), p(t), \mu(t)) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), p(t), \lambda(t)) + \bar{g} (t, q(t), v(t), p(t), \mu(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) , \\
0 &= \phi (t, q(t), v(t), p(t)) , \\
0 &= \psi (t, q(t), v(t), p(t), \dot{q}(t), \dot{p}(t)) ,
\end{aligned}
$$

運動量 $p$ と力場 $f$ は次のように与えられます。

$$
\begin{aligned}
p &= \frac{\partial L}{\partial v} (q,v) , &
f &= \frac{\partial L}{\partial q} (q,v) ,
\end{aligned}
$$

射影場 $u$, $\bar{u}$ および $g$, $\bar{g}$。これは、動的変数 $(q,p)$ と代数変数 $v$, $\lambda$ および $\mu$ を持つ微分代数方程式の特別なケースです。

初期条件 $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ を持つ動的変数 $(q,p)$ は $\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取ります。初期条件 $(λ(t_{0}) = λ_{0}, μ(t_{0}) = μ_{0})$ を持つ代数変数 $(λ,μ)$ は $\mathbb{R}^{m} \times \mathbb{R}^{m}$ の値を取ります。

### コンストラクタ

```julia
LDAEProblem(ϑ, f, u, g, ϕ, ū, ḡ, ψ, ω, l, tspan, tstep, ics; kwargs...)
LDAEProblem(ϑ, f, u, g, ϕ, ū, ḡ, ψ, ω, l, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable = zero(q₀), μ₀::StateVariable = zero(λ₀); kwargs...)
LDAEProblem(ϑ, f, u, g, ϕ, ω, l, tspan, tstep, ics; kwargs...)
LDAEProblem(ϑ, f, u, g, ϕ, ω, l, tspan, tstep, q₀::StateVariable, p₀::StateVariable, λ₀::StateVariable = zero(q₀); kwargs...)
```

関数 `ϑ` は運動量を計算し、`f` は力場を計算し、`u` と `g` は射影を計算し、`ϕ` は代数制約を提供します。関数 `ψ`, `ū` および `ḡ` はオプションであり、代数制約の時間微分と対応する射影を提供します。

`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップであり、`ics` は `NamedTuple` で `q` と `p` のエントリを持ちます。初期条件 `q₀`, `p₀`, `λ₀` および `μ₀` も直接指定でき、`StateVariable` は `AbstractArray{<:Number}` です。関数 `ϑ`, `f`, `u`, `g`, `ϕ`, `ū`, `ḡ`, `ψ`, `ω` および `l` のインターフェースについては [`LDAE`](@ref) を参照してください。

[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに対する標準のキーワード引数に加えて、`LDAEProblem` は初期推定値の計算のために関数 `v̄` と `f̄` を受け入れ、デフォルト値は `v̄ = _ldae_default_v̄` および `f̄ = f` です。

### 関数定義

関数 `ϑ` と `f` は次のインターフェースを持たなければなりません。

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

ここで `t` は現在の時間、`q` は現在の解ベクトル、`v` は現在の速度であり、`f` と `p` は関数 $f$ と $ϑ$ を `t`, `q` および `v` で評価した結果を保持するベクトルです。関数 `g`, `v̄` および `f̄` は次のように指定されます。

```julia
function u(u, t, q, v, p, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function g(g, t, q, v, p, μ, params)
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

関数 `ω` と `l` は、シンプレクティック行列とラグランジュを計算し、次のシグネチャを持ちます。

```julia
function ω(f, t, q, v, params)
    ω[1,1] = ...
    ω[1,2] = ...
    ...
end

function l(t, q, v, params)
    return ...
end
```

一部の積分器は、二次制約 $\psi$ を強制し、次の追加関数を要求します。

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

上記の関数定義を使用して、`LDAEProblem` は次のように作成できます。

```julia
tspan = (0.0, 1.0)
tstep = 0.1
q₀ = [1., 1.]
p₀ = [1., 0.]
λ₀ = [0.]
μ₀ = [0.]

prob = LDAEProblem(ϑ, f, u, g, ϕ, ω, l, tspan, tstep, q₀, p₀, λ₀)
```

または

```julia
prob = LDAEProblem(ϑ, f, u, g, ϕ, ū, ḡ, ψ, ω, l, tspan, tstep, q₀, p₀, λ₀, μ₀)
```
