`PDAE`: 分割微分代数方程

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

### パラメータ

  * `vType <: Callable`: `v` の型
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

  * `v`: ベクトル場 $v$ を計算する関数
  * `f`: ベクトル場 $f$ を計算する関数
  * `u`: $q$ のための射影を計算する関数
  * `g`: $p$ のための射影を計算する関数
  * `ϕ`: 代数制約
  * `ū`: 二次射影場 $\bar{u}$ を計算する関数 (*オプション*)
  * `ḡ`: 二次射影場 $\bar{g}$ を計算する関数 (*オプション*)
  * `ψ`: 二次制約 (*オプション*)
  * `v̄`: 速度場 $v$ の初期推定を計算する関数 (*オプション*, デフォルトは `v`)
  * `f̄`: 力場 $f$ の初期推定を計算する関数 (*オプション*, デフォルトは `f`)
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
PDAE(v, f, u, g, ϕ, ū, ḡ, ψ, v̄, f̄, invariants, parameters, periodicity)
PDAE(v, f, u, g, ϕ, ū, ḡ, ψ; kwargs...)
PDAE(v, f, u, g, ϕ; kwargs...)
```

関数 `v` と `f` はベクトル場を計算し、`u` と `g` は射影を計算し、`ϕ` は代数制約を提供します。関数 `ψ`、`ū` および `ḡ` はオプションであり、二次制約と対応する射影を提供します。

### 関数定義

関数は次のように定義されます

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

ここで `t` は現在の時間、`q`、`p` および `λ` は現在の解ベクトル、`v`、`f`、`u` および `g` はベクトル場 $v$ と $f$ の評価結果を保持するベクトル、射影 $u$ と $g$、そして `ϕ` は `t`、`q`、`p` および `λ` に対して評価された代数制約 $\phi$ を保持します。

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

`PDAE` は次のように作成されます

```julia
equ = PDAE(v, f, u, g, ϕ)
```

または

```julia
equ = PDAE(v, f, u, g, ϕ, ū, ḡ, ψ)
```
