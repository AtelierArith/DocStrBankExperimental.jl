`PSDE`: ストラトノビッチ分割確率微分方程式

分割確率微分方程式は、次の形の初期値問題です。

$$
\begin{aligned}
dq (t) &= v(t, q(t), p(t)) \, dt + B(t, q(t), p(t)) \circ dW , & q(t_{0}) &= q_{0} , \\
dp (t) &= f(t, q(t), p(t)) \, dt + G(t, q(t), p(t)) \circ dW , & p(t_{0}) &= p_{0}
\end{aligned}
$$

ドリフトベクトル場 $v$ と $f$、拡散行列 $B$ と $G$、初期条件 $q_{0}$ と $p_{0}$、動的変数 $(q,p)$ は $\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取り、m次元ウィーナー過程 W があります。

### パラメータ

  * `vType <: Callable`: `v` の型
  * `fType <: Callable`: `f` の型
  * `BType <: Callable`: `B` の型
  * `GType <: Callable`: `G` の型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `v`: 位置変数 $q$ のドリフトベクトル場を計算する関数
  * `f`: 運動量変数 $p$ のドリフトベクトル場を計算する関数
  * `B`: 位置変数 $q$ の d x m 拡散行列を計算する関数
  * `G`: 運動量変数 $p$ の d x m 拡散行列を計算する関数
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
PSDE(v, f, B, G, invariants, parameters, periodicity)
PSDE(v, f, B, G; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

関数 `v`、`f`、`B` および `G` は、ドリフトベクトル場と拡散行列を提供し、それぞれ5つの引数を取ります。`v(v, t, q, p, params)`、`f(f, t, q, p, params)`、`B(B, t, q, p, params)` および `G(G, t, q, p, params)` で、ここで `t` は現在の時間、`(q, p)` は現在の解、`v`、`f`、`B` および `G` はベクトル場 $v$、$f$ および行列 $B$、$G$ を `t` と `(q,p)` に対して評価した結果を保持する変数であり、`params` はオプションのパラメータです。

対応するメソッドは次のシグネチャを持つべきです。

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

function B(B, t, q, p, params)
    B[1,1] = ...
    ...
end

function G(G, t, q, p, params)
    G[1,1] = ...
    ...
end
```
