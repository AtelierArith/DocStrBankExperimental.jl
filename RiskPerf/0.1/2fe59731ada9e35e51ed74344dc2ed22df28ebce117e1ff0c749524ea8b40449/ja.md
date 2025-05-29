```
information_ratio(asset_returns, benchmark_returns; multiplier=1.0)
```

この関数は、アクティブリターンをトラッキングエラーで割った値として情報比率を計算します。この計算は、ウィリアム・F・シャープのシャープ比の元のバージョンの改訂版に等しいです（関数 `sharpe_ratio` を参照）。

# 数式

$$
\text{IR} = \dfrac{\mathbb{E}\left[\text{asset\_returns} - \text{benchmark\_returns} \right]}{\sigma(\text{asset\_returns} - \text{benchmark\_returns})} \times \sqrt{\text{multiplier}}
$$

# 引数

  * `asset_returns`:      資産リターンのベクトル。
  * `benchmark_returns`:  提供されたリターンと同じ頻度（例：日次）を持つベンチマークリターンのベクトルまたはスカラー値。
  * `multiplier`:         オプションのスカラー乗数。すなわち、月次リターンを年換算するには `12` を使用し、日次リターンを年換算するには `252` を使用します。

# 出典

  * Sharpe, William F. (1994). "The Sharpe Ratio". The Journal of Portfolio Management.
