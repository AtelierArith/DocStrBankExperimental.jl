```
vegas(f, st, en, kwargs...)
```

VEGASは、適応重要度サンプリングに基づく多次元積分のためのモンテカルロアルゴリズムです。各次元をビンに分割し、関数の大きさが最も高い領域からサンプリングされるポイントのためにビンの幅を適応的に調整します。

## 引数:

  * st: 各次元の開始値の配列。

デフォルトはzeros(2)

  * end: 各次元の終了値の配列。

デフォルトはones(2)

## Kwargs:

  * nbins: 各次元のビンの数。

デフォルトは1000。

  * ncalls: 各イテレーションあたりの関数呼び出しの数。

デフォルトは10000。

  * maxiter: 最大イテレーション数。

デフォルトは10。

  * rtol: 必要な相対許容誤差。

デフォルトは1e-4。

  * atol: 必要な絶対許容誤差。

デフォルトは1e-2。

  * debug: 100イテレーションごとに`abs(sd/I)`を表示します。

デフォルトはfalse。

  * batch: `f`が関数評価のバッチを返すかどうか。

`f`は1つの引数`pts`を取り、`ncalls × ndims`の行列を想定します。各行はユニークなポイントで、`ncalls`の長さの関数評価のベクトルを返します。この引数のデフォルトはfalseです。

## 出力:

以下のフィールドを持つVEGASResultオブジェクト:

  * 積分の推定値
  * 標準偏差
  * χ^2 / (numiter - 1): 1未満であるべき

そうでなければ、積分の推定値は信頼できません。

  * 最終的に適応されたマップ

## 参考文献:

  * Lepage, G. Peter. "A new algorithm for adaptive

multidimensional integration." Journal of  Computational Physics 27.2 (1978): 192-203.

  * Lepage, G. Peter. "Adaptive multidimensional

integration: VEGAS enhanced." Journal of  Computational Physics 439 (2021): 110386. ```
