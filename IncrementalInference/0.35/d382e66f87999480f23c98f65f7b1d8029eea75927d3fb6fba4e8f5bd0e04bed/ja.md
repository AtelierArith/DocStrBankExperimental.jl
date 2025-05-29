```julia
mutable struct FactorGradientsCached!{F<:DistributedFactorGraphs.AbstractRelative, S, M, P, G, L}
```

ファクター上で勾配を計算するためのコンテナ。ヘルパーコンストラクタ関数を参照してください。

2つの変数間の1つの関数 $f$ に基づくグラフと測定値 $z$ を取ります。

```
(:x1)-[:x1x2f1]-(:x2)
```

勾配（座標に作用する行列）は、次のように定義されます $(▽f - I)$

$$
0 = (▽ f - I) dC
$$

ここで、拡張された座標ベクトルは $dC = [dX_1, dX_2]'$ です。アイデアは、$dC$ が通常の偏微分（ベクトル）分解に従って $(▽f - I)$ のヌル空間にあるべきであるということです；

$$
dX_1 = {∂f}/{∂X_2'} dX_2 + ...
$$

座標でモデル化されています。

ノート

  * メモリはオブジェクトにキャッシュされています。
  * 勾配はオブジェクトへのファンクタ呼び出しとして更新されます。例を参照してください。
  * ファクターは、計算されたファクター残差に `_slack` として現れる「張力または圧縮」にあると仮定されています。これもキャッシュされています。

開発ノート

  * TODO 型の安定性
  * TODO インプレースメモリ操作
  * TODO 硬い座標の仮定を緩和し、代わりに多様体接空間 $T_f M$ での直接的な演算子定義を許可します。

例

```julia
# 問題セット
pp = LinearRelative(MvNormal([10;0],[1 0; 0 1]))
measurement = ([10.0;0.0],)
varTypes = (ContinuousEuclid{2}, ContinuousEuclid{2})
pts = ([0;0.0], [9.5;0])

# ファンクタオブジェクトを構築して評価
grad = FactorGradientsCached!(pp, varTypes, measurement, pts);
J = grad(measurement..., pts...)

# キャッシュされた値が保存される
J_ = grad.cached_gradients

# すべてが機能していることを再確認
@assert norm(J_ - J) < 1e-6 
```

関連

[`calcFactorResidualTemporary`](@ref), [`_buildGraphByFactorAndTypes`](@ref)
