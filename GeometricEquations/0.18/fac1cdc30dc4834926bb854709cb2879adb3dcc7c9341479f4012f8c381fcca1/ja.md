`DAEProblem`: 微分代数方程問題

微分代数初期値問題を定義します

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t)) + u(t, q(t), \lambda(t)) , \\
0 &= \phi (t, q(t)) ,
\end{aligned}
$$

ベクトル場 $v$、射影 $u$、代数制約 $\phi=0$ を持ちます。

いくつかの積分器は、代数制約 $\phi$ の時間微分である二次制約 $\psi$ も強制します。この場合、方程式の系は次のように修正されます

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t)) + u(t, q(t), \lambda(t)) + \bar{u} (t, q(t), \dot{q} (t), \dot{p} (t), \mu(t)) , \\
0 &= \phi (t, q(t)) , \\
0 &= \psi (t, q(t), \dot{q} (t)) .
\end{aligned}
$$

動的変数 $q$ は初期条件 $q(t_{0}) = q_{0}$ を持ち、$\mathbb{R}^{d}$ の値を取ります。代数変数 $(λ,μ)$ は初期条件 $(λ(t_{0}) = λ_{0}, μ(t_{0}) = μ_{0})$ を持ち、$\mathbb{R}^{m} \times \mathbb{R}^{m}$ の値を取ります。

### コンストラクタ

```julia
DAEProblem(v, u, ϕ, ū, ψ, tspan, tstep, ics::NamedTuple; kwargs...)
DAEProblem(v, u, ϕ, ū, ψ, tspan, tstep, q₀::StateVariable, λ₀::StateVariable, μ₀::StateVariable = zero(λ₀); kwargs...)
DAEProblem(v, u, ϕ, tspan, tstep, ics::NamedTuple; kwargs...)
DAEProblem(v, u, ϕ, tspan, tstep, q₀::StateVariable, λ₀::StateVariable; kwargs...)
```

関数 `v` と `u` はそれぞれベクトル場と射影を計算し、`ϕ` は代数制約を提供します。関数 `ψ` と `ū` はオプションで、代数制約の時間微分である二次制約と対応する射影を提供します。

`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップで、`ics` は `q`、`λ`、`μ` のエントリを持つ `NamedTuple` です。初期条件 `q₀`、`λ₀`、`μ₀` は直接指定することもでき、`StateVariable` は `AbstractArray{<:Number}` です。関数 `v`、`u`、`ϕ`、`ū`、`ψ` のインターフェースについては [`DAE`](@ref) を参照してください。

[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに対する標準のキーワード引数に加えて、`DAEProblem` はベクトル場の初期推定を計算するための関数 `v̄` を受け入れ、デフォルト値は `v̄ = v` です。

### 関数定義

関数 `v`、`u`、`ϕ` は次のインターフェースを持たなければなりません

```julia
function v(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end

function u(u, t, q, λ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ϕ(ϕ, t, q, params)
    ϕ[1] = ...
end
```

ここで `t` は現在の時間、`q` と `λ` は現在の解ベクトルであり、`v`、`u`、`ϕ` は `t`、`q`、`λ` におけるベクトル場 $v$、射影 $u$、代数制約 $\phi$ の評価結果を保持するベクトルです。

いくつかの積分器は二次制約 $\psi$ も強制し、次の追加関数を必要とします

```
function ū(u, t, q, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ψ(ψ, t, q, v, params)
    ψ[1] = ...
end
```

上記の関数定義を使用して `DAEProblem` を作成することができます

```julia
tspan = (0.0, 1.0)
tstep = 0.1
q₀ = [1., 1.]
λ₀ = [0.]
μ₀ = [0.]

prob = DAEProblem(v, u, ϕ, tspan, tstep, q₀, λ₀)
```

または

```julia
prob = DAEProblem(v, u, ϕ, ū, ψ, tspan, tstep, q₀, λ₀, μ₀)
```
