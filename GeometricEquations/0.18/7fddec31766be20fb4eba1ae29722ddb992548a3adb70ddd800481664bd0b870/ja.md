`IDAE`: 暗黙の微分代数方程式

暗黙の微分代数初期値問題は次の形を取ります

$$
\begin{aligned}
\dot{q} (t) &= v(t) + u(t, q(t), v(t), p(t), \lambda(t)) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), p(t), \lambda(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) , \\
0 &= \phi (t, q(t), v(t), p(t)) ,
\end{aligned}
$$

力場 $f$、$ϑ$ によって定義される運動量、射影 $u$ と $g$、代数制約 $\phi(t,q,v,p)=0$ があります。

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

### パラメータ

  * `ϑType <: Callable`: `ϑ` の型
  * `fType <: Callable`: `f` の型
  * `uType <: Callable`: `u` の型
  * `gType <: Callable`: `g` の型
  * `ϕType <: Callable`: `ϕ` の型
  * `ūType <: Callable`: `ū` の型
  * `ḡType <: Callable`: `ḡ` の型
  * `ψType <: Callable`: `ψ` の型
  * `v̄Type <: Callable`: `v̄` の型
  * `f̄Type <: Callable`: `f̄` の型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `ϑ`: 運動量を決定する関数
  * `f`: ベクトル場 $f$ を計算する関数
  * `u`: $q$ の射影を計算する関数
  * `g`: $p$ の射影を計算する関数
  * `ϕ`: 代数制約
  * `ū`: 二次射影場 $\bar{u}$ を計算する関数 (*オプション*)
  * `ḡ`: 二次射影場 $\bar{g}$ を計算する関数 (*オプション*)
  * `ψ`: 二次制約 (*オプション*)
  * `v̄`: 速度場 $v$ の初期推定を計算する関数 (*オプション*)
  * `f̄`: 力場 $f$ の初期推定を計算する関数 (*オプション*)
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
IDAE(ϑ, f, u, g, ϕ, ū, ḡ, ψ, v̄, f̄, invariants, parameters, periodicity)
IDAE(ϑ, f, u, g, ϕ, ū, ḡ, ψ; v̄ = _idae_default_v̄, f̄ = f, invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
IDAE(ϑ, f, u, g, ϕ; v̄ = _idae_default_v̄, f̄ = f, invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

ここで 

```julia
_idae_default_v̄(v, t, q, params) = nothing
```

関数 `ϑ` は運動量を計算し、`f` は力場を計算し、`u` と `g` は射影を計算し、`ϕ` は代数制約を提供します。関数 `ψ`、`ū` および `ḡ` はオプションであり、代数制約の時間微分である二次制約と対応する射影を提供します。

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

いくつかの積分器は二次制約 $\psi$ も強制し、次の追加関数を必要とします

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
