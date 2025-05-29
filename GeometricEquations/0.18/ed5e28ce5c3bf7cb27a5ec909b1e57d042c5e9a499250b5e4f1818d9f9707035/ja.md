`LDAE`: ラグランジュ微分代数方程式

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

射影場 $u$, $\bar{u}$ と $g$, $\bar{g}$。これは、動的変数 $(q,p)$ と代数変数 $v$, $\lambda$ と $\mu$ を持つ微分代数方程式の特別なケースです。

### パラメータ

  * `ϑType <: Callable`: `ϑ` の型
  * `fType <: Callable`: `f` の型
  * `uType <: Callable`: `u` の型
  * `gType <: Callable`: `g` の型
  * `ϕType <: Callable`: `ϕ` の型
  * `ūType <: Callable`: `ū` の型
  * `ḡType <: Callable`: `ḡ` の型
  * `ψType <: Callable`: `ψ` の型
  * `ωType <: Callable`: `ω` の型
  * `v̄Type <: Callable`: `v̄` の型
  * `f̄Type <: Callable`: `f̄` の型
  * `lagType <: Callable`: ラグランジュ型
  * `invType <: OptionalInvariants`: 不変量型
  * `parType <: OptionalParameters`: パラメータ型
  * `perType <: OptionalPeriodicity`: 周期性型

### フィールド

  * `f`: ベクトル場を計算する関数
  * `u`: $\lambda$ によって与えられる退化系のための $q$ の射影を計算する関数
  * `g`: $\nabla \vartheta (q) \cdot \lambda$ によって与えられる退化系のための $p$ の射影を計算する関数
  * `ϕ`: $p - \vartheta (t,q)$ によって与えられる退化系のための主制約
  * `ū`: $\lambda$ によって与えられる退化系のための二次射影場 $\bar{u}$ を計算する関数 (*オプション*)
  * `ḡ`: $\lambda \cdot \nabla \vartheta (t,q)$ によって与えられる退化系のための二次射影場 $\bar{g}$ を計算する関数 (*オプション*)
  * `ψ`: $\dot{p} - \dot{q} \cdot \nabla \vartheta (t,q)$ によって与えられる退化系のための二次制約 (*オプション*)
  * `ω`: シンプレクティック行列を計算する関数
  * `v̄`: 速度場 $v$ の初期推定を計算する関数 (*オプション*)
  * `f̄`: 力場 $f$ の初期推定を計算する関数 (*オプション*)
  * `lagrangian`: ラグランジュ $L$ を計算する関数
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
LDAE(ϑ, f, u, g, ϕ, ū, ḡ, ψ, ω, v̄, f̄, lagrangian, invariants, parameters, periodicity)
LDAE(ϑ, f, u, g, ϕ, ū, ḡ, ψ, ω, lagrangian; v̄ = _ldae_default_v̄, f̄ = f, invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
LDAE(ϑ, f, u, g, ϕ, ω, lagrangian; v̄ = _ldae_default_v̄, f̄ = f, invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

ここで 

```julia
_ldae_default_v̄(v, t, q, params) = nothing
```

関数 `ϑ` は運動量を計算し、`f` は力場を計算し、`u` と `g` は射影を計算し、`ϕ` は代数制約を提供します。関数 `ψ`, `ū` と `ḡ` はオプションであり、代数制約の時間微分と対応する射影を提供します。

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

ここで `t` は現在の時間、`q` は現在の解ベクトル、`v` は現在の速度であり、`f` と `p` は関数 $f$ と $ϑ$ を `t`, `q` と `v` で評価した結果を保持するベクトルです。関数 `g`, `v̄` と `f̄` は次のように指定されます。

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

そして、シンプレクティック行列とラグランジュを計算する関数 `ω` と `l` は次のシグネチャを持ちます。

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

一部の積分器は二次制約 $\psi$ を強制し、次の追加関数を必要とします。

```
function ū(u, t, q, v, p, μ, params)
    u[1] = ...
    u[2] = ...
    ...
end

function ḡ(g, t, q, v, p, μ, params)
    g[1] = ...
    g[2] = ...
end

function ψ(ψ, t, q, v, p, q̇, ṗ, params)
    ψ[1] = ...
end
```
