`LODE`: ラグランジュ常微分方程式

ラグランジュ系の方程式は、暗黙の常微分方程式の特別なケースであり、次の形式の暗黙の初期値問題です。

$$
\begin{aligned}
\dot{q} (t) &= v(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

運動量 $p$ と力場 $f$ によって与えられます。

$$
\begin{aligned}
p &= \frac{\partial L}{\partial v} , &
f &= \frac{\partial L}{\partial q} .
\end{aligned}
$$

これは、ラグランジュによって定義された暗黙の常微分方程式の特別なケースであり、動的変数 $(q,p)$ と代数変数 $v$ を持つ微分代数方程式の特別なケースでもあり、制約 $p(t) = ϑ(t, q(t), v(t))$ が満たされるように決定されます。

多くの積分器は、この制約を強制するために投影ステップを実行します。この目的のために、システムは次のように拡張されます。

$$
\begin{aligned}
\dot{q} (t) &= v(t) + \lambda(t) , \\
\dot{p} (t) &= f(t, q(t), v(t)) + g(t, q(t), v(t), \lambda(t)) , \\
p(t) &= ϑ(t, q(t), v(t)) ,
\end{aligned}
$$

ここで、投影ステップを定義するベクトル場は通常次のように与えられます。

$$
\begin{aligned}
g(t, q(t), v(t), λ(t)) &= λ(t) \cdot \nabla ϑ(t, q(t), v(t)) .
\end{aligned}
$$

### パラメータ

  * `ϑType <: Function`: `ϑ` の型
  * `fType <: Function`: `f` の型
  * `gType <: Function`: `g` の型
  * `ωType <: Function`: `ω` の型
  * `v̄Type <: Function`: `v̄` の型
  * `f̄Type <: Function`: `f̄` の型
  * `lagType <: Function`: ラグランジュ型
  * `invType <: OptionalInvariants`: 不変量型
  * `parType <: OptionalParameters`: パラメータ型
  * `perType <: OptionalPeriodicity`: 周期性型

### フィールド

  * `ϑ`: 運動量を決定する関数
  * `f`: ベクトル場を計算する関数
  * `g`: 投影を決定する関数、$\nabla \vartheta (q) \cdot \lambda$ によって与えられる
  * `ω`: シンプレクティック行列を計算する関数
  * `v̄`: 速度場 $v$ の初期推定を計算する関数（オプション）
  * `f̄`: 力場 $f$ の初期推定を計算する関数（オプション）
  * `lagrangian`: ラグランジュ $L$ を計算する関数
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
LODE(ϑ, f, g, ω, l, v̄, f̄, invariants, parameters, periodicity)
LODE(ϑ, f, g, ω, l; v̄ = _lode_default_v̄, f̄ = f, invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

ここで 

```julia
_lode_default_v̄(v, t, q, params) = nothing
```

### 関数定義

関数 `ϑ` と `f` は次のインターフェースを持たなければなりません。

```julia
function ϑ(p, t, q, v)
    p[1] = ...
    p[2] = ...
    ...
end
```

および

```julia
function f(f, t, q, v)
    f[1] = ...
    f[2] = ...
    ...
end
```

ここで `t` は現在の時間、`q` は現在の解ベクトル、`v` は現在の速度であり、`f` と `p` は関数 $f$ と $ϑ$ を `t`、`q`、`v` で評価した結果を保持するベクトルです。関数 `g`、`v̄`、および `f̄` は次のように指定されます。

```julia
function g(g, t, q, λ)
    g[1] = ...
    g[2] = ...
    ...
end
```

および

```julia
function v̄(v, t, q, p)
    v[1] = ...
    v[2] = ...
    ...
end

function f̄(f, t, q, v)
    f[1] = ...
    f[2] = ...
    ...
end
```

関数 `g` は $p = ϑ(q)$ を強制する投影法で使用されます。関数 `v̄` と `f̄` は非線形暗黙のソルバーにおける初期推定に使用されます。最後に、シンプレクティック行列とラグランジュを計算する関数 `ω` と `l` は次のシグネチャを持ちます。

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
