`ODE`: 常微分方程

常微分方程は、次の形の初期値問題を定義します。

$$
\dot{q} (t) = v(t, q(t)) ,
$$

ベクトル場 $v$ を用いて。

### パラメータ

  * `vType <: Callable`: `v` の型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `v`: ベクトル場を計算する関数
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切り取るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
ODE(v, invariants, parameters, periodicity)
ODE(v; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

### 関数定義

ベクトル場を提供する関数 `v` は、次のインターフェースを持たなければなりません。

```julia
function v(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

ここで、`t` は現在の時間、`q` は現在の解ベクトル、`v` は `t` と `q` に対してベクトル場 $v$ を評価した結果を保持するベクトル、`params` はベクトル場が依存する可能性のある追加のパラメータの `NamedTuple` です。
