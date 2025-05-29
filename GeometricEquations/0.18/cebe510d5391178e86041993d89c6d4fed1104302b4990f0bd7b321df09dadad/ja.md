`HDAE`: ハミルトン微分代数方程式

ハミルトン微分代数方程式は、ディラック制約に従った標準的なハミルトン系の方程式である初期値問題です。

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) + u(t, q(t), p(t), \lambda(t)) + \bar{u} (t, q(t), p(t), \mu(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) + g(t, q(t), p(t), \lambda(t)) + \bar{g} (t, q(t), p(t), \mu(t)) , \\
0 &= \phi (t, q(t), p(t)) , \\
0 &= \psi (t, q(t), p(t), \dot{q}(t), \dot{p}(t)) ,
\end{aligned}
$$

ベクトル場 $v$, $u$, $\bar{u}$ と $f$, $g$, $\bar{g}$、一次制約 $\phi(q,p)=0$ および二次制約 $\psi(q,p,\dot{q},\dot{p})=0$ があります。

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
  * `hamType <: Callable`: ハミルトニアンの型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `v`: ハミルトンベクトル場 $v$ を計算する関数
  * `f`: ハミルトンベクトル場 $f$ を計算する関数
  * `u`: $q$ の射影を計算する関数
  * `g`: 一次射影場 $g$ を計算する関数
  * `ϕ`: 一次制約
  * `ū`: 二次射影場 $\bar{u}$ を計算する関数 (*オプション*)
  * `ḡ`: 二次射影場 $\bar{g}$ を計算する関数 (*オプション*)
  * `ψ`: 二次制約 (*オプション*)
  * `v̄`: 速度場 $v$ の初期推定を計算する関数 (*オプション*, デフォルトは `v`)
  * `f̄`: 力場 $f$ の初期推定を計算する関数 (*オプション*, デフォルトは `f`)
  * `hamiltonian`: ハミルトニアン $H$ を計算する関数（通常はシステムの総エネルギー）
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
HDAE(v, f, u, g, ϕ, ū, ḡ, ψ, h, v̄, f̄, invariants, parameters, periodicity)
HDAE(v, f, u, g, ϕ, ū, ḡ, ψ, h; kwargs...)
HDAE(v, f, u, g, ϕ, h; kwargs...)
```

関数 `v` と `f` はベクトル場を計算し、`u` と `g` は射影を計算し、`ϕ` は代数制約を提供し、`h` はハミルトニアンを提供します。関数 `ψ`, `ū` および `ḡ` はオプションであり、代数制約の時間微分と対応する射影を提供します。

### 関数定義

関数は次のように定義されます。

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

ここで `t` は現在の時間、`q`, `p`, `λ` および `μ` は現在の解ベクトル、`v`, `f`, `u` および `g` はベクトル場 $v$ と $f$ の評価結果、一次制約 $u$ と $g$ の射影を保持し、`ϕ` は代数制約 $\phi$ を保持し、`h` はシステムのハミルトニアンを返します。すべて `t`, `q`, `p` および `λ` で評価されます。

一部の積分器は二次制約 $\psi$ を強制し、次の追加関数を必要とします。

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

`HDAE` は次のように作成されます。

```julia
equ = HDAE(v, f, u, g, ϕ, h)
```

または

```julia
equ = HDAE(v, f, u, g, ϕ, ū, ḡ, ψ, h)
```
