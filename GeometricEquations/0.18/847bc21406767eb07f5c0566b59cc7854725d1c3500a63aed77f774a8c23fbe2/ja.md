`DAE`: 微分代数方程

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

### パラメータ

  * `vType <: Callable`: `v` の型
  * `uType <: Callable`: `u` の型
  * `ϕType <: Callable`: `ϕ` の型
  * `ūType <: OptionalCallable`: `ū` の型
  * `ψType <: OptionalCallable`: `ψ` の型
  * `v̄Type <: Callable`: `v̄` の型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `v`: ベクトル場 `v(v, t, q, params)` を計算する関数
  * `u`: 射影 `u(u, t, q, λ, params)` を計算する関数
  * `ϕ`: 代数制約 `ϕ(ϕ, t, q, params)`
  * `ū`: 二次射影場 `ū(ū, t, q, λ, params)` を計算する関数 (*オプション*)
  * `ψ`: 二次制約 `ψ(ψ, t, q, v, params)` (*オプション*)
  * `v̄`: 速度場 $v$ の初期推定を計算する関数（デフォルトは `v`）
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
DAE(v, u, ϕ, ū, ψ, v̄, invariants, parameters, periodicity)
DAE(v, u, ϕ, ū, ψ; kwargs...)
DAE(v, u, ϕ; kwargs...)
```

関数 `v` と `u` はそれぞれベクトル場と射影を計算し、`ϕ` は代数制約を提供します。関数 `ψ` と `ū` はオプションで、代数制約の時間微分である二次制約と対応する射影を提供します。

### 関数定義

関数は次のように定義されます

関数 `v`、`u` および `ϕ` は次のインターフェースを持たなければなりません

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

ここで `t` は現在の時間、`q` と `λ` は現在の解ベクトルであり、`v`、`u` および `ϕ` は `t`、`q` および `λ` におけるベクトル場 $v$、射影 $u$ および代数制約 $\phi$ の評価結果を保持するベクトルです。

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

`DAE` は次のように作成されます

```julia
equ = DAE(v, u, ϕ)
```

または

```julia
equ = DAE(v, u, ϕ, ū, ψ)
```
