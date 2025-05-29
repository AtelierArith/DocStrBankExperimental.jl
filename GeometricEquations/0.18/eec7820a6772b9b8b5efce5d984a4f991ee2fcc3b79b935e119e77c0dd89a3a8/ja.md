`SPSDE`: ストラトノビッチ分割確率微分方程式

分割された確率微分初期値問題を定義します

$$
\begin{aligned}
dq (t) &=   v(t, q(t), p(t)) \, dt + B(t, q(t), p(t)) \circ dW , & q(t_{0}) &= q_{0} , \\
dp (t) &= [ f_1(t, q(t), p(t)) + f_2(t, q(t), p(t)) ] \, dt + [ G_1(t, q(t), p(t)) + G_2(t, q(t), p(t)) ] \circ dW , & p(t_{0}) &= p_{0} ,
\end{aligned}
$$

ドリフトベクトル場 $v$ と $f_i$、拡散行列 $B$ と $G_i$、初期条件 $q_{0}$ と $p_{0}$、動的変数 $(q,p)$ が $\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取り、m次元ウィーナー過程 W があります。

### パラメータ

  * `vType <: Function`: `v` の型
  * `f1Type <: Function`: `f1` の型
  * `f2Type <: Function`: `f2` の型
  * `BType <: Function`: `B` の型
  * `G1Type <: Function`: `G1` の型
  * `G2Type <: Function`: `G2` の型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `v` :  位置変数 $q$ のドリフトベクトル場を計算する関数
  * `f1`:  運動量変数 $p$ のドリフトベクトル場を計算する関数
  * `f2`:  運動量変数 $p$ のドリフトベクトル場を計算する関数
  * `B` :  位置変数 $q$ の d x m 拡散行列を計算する関数
  * `G1`:  運動量変数 $p$ の d x m 拡散行列を計算する関数
  * `G2`:  運動量変数 $p$ の d x m 拡散行列を計算する関数
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む `NamedTuple` または `NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む `NamedTuple` または `NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル `q` の周期性を決定する、`AbstractArray` または `NullPeriodicity`

### コンストラクタ

```julia
SPSDE(v, f1, f2, B, G1, G2, invariants, parameters, periodicity)
SPSDE(v, f1, f2, B, G1, G2; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

関数 `v`, `f1`, `f2`, `B`, `G1` および `G2` は、ドリフトベクトル場と拡散行列を提供し、すべて5つの引数 `(out, t, q, p, params)` を取ります。

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f1(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function f2(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function B(B, t, q, p, params)
    B[1,1] = ...
    ...
end

function G1(G, t, q, p, params)
    G[1,1] = ...
    ...
end

function G2(G, t, q, p, params)
    G[1,1] = ...
    ...
end
```

ここで `t` は現在の時間、`(q,p)` は現在の解ベクトルであり、`v`, `f`, `B` および `G` はベクトル場 $v$, $f$ および行列 $B_i$, $G_i$ を `(t,q,p)` で評価した結果を保持する変数です。
