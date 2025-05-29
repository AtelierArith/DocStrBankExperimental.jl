`SDE`: ストラトノビッチ確率微分方程式

確率微分初期値問題を定義します

$$
\begin{aligned}
dq (t) &= v(t, q(t)) \, dt + B(t, q(t)) \circ dW , & q(t_{0}) &= q_{0} ,
\end{aligned}
$$

ドリフトベクトル場 $v$、拡散行列 $B$、初期条件 $q_{0}$、動的変数 $q$ が $\mathbb{R}^{d}$ の値を取り、m次元ウィーナー過程 W があります。

### パラメータ

  * `vType <: Callable`: `v` の型
  * `BType <: Callable`: `B` の型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `v`: 決定論的ベクトル場を計算する関数
  * `B`: d x m の拡散行列を計算する関数
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切り取るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
SDE(v, B, invariants, parameters, periodicity)
SDE(v, B; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

ドリフトベクトル場と拡散行列を提供する関数 `v` と `B`。関数 `v` は次のインターフェースを持たなければなりません。

```julia
function v(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

ここで `t` は現在の時間、`q` は現在の解ベクトル、`v` は `t` と `q` に対してベクトル場 $v$ を評価した結果を保持するベクトル、params は追加のパラメータです。関数 `B` は次のインターフェースを持つメソッドを持つべきです。

```julia
function B(B, t, q, params)
    B[1,1] = ...
    ...
end
```
