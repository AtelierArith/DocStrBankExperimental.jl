`HODE`: ハミルトン常微分方程式

標準的なハミルトン系の方程式は、分割された常微分方程式の特別なケースです。

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) ,
\end{aligned}
$$

ベクトル場 $v$ と $f$ は次のように与えられます。

$$
\begin{aligned}
v &=   \frac{\partial H}{\partial p} , &
f &= - \frac{\partial H}{\partial q} .
\end{aligned}
$$

### パラメータ

  * `vType <: Callable`: `v` の型
  * `fType <: Callable`: `f` の型
  * `hamType <: Callable`: ハミルトン型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `v`: ベクトル場 $v$ を計算する関数
  * `f`: ベクトル場 $f$ を計算する関数
  * `hamiltonian`: ハミルトン $H$ を計算する関数（通常はシステムの総エネルギー）
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
HODE(v, f, hamiltonian, invariants, parameters, periodicity)
HODE(v, f, hamiltonian; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

### 関数定義

関数 `v`、`f` および `hamiltonian` は次のインターフェースを持たなければなりません。

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function hamiltonian(t, q, p, params)
    return ...
end
```

ここで `t` は現在の時間、`q` と `p` は現在の解ベクトル、`v` と `f` は `t`、`q` および `p` に対してベクトル場を評価した結果を保持するベクトルであり、`params` は追加のパラメータの `NamedTuple` です。
