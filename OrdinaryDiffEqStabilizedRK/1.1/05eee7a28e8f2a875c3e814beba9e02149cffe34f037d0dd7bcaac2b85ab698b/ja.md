```
ESERK4(; eigen_est = nothing)
```

J. Martín-Vaquero, B. Kleefeld. 外挿安定化明示ルンゲ-クッタ法, 計算物理学ジャーナル, 326, pp 141-155, 2016. doi: https://doi.org/10.1016/j.jcp.2016.08.042.

ESERK4: 安定化明示法。第四次外挿安定化ルンゲ-クッタ法。実固有値に対して高い安定性を示し、中程度の大きさの複素固有値を許容するように滑らかにされています。

この方法は、次の形式のキーワード引数 `eigen_est` を取ります。

`eigen_est = (integrator) -> integrator.eigen_est = upper_bound`,

ここで `upper_bound` はヤコビ行列のスペクトル半径の推定上限です。`eigen_est` が提供されない場合、`upper_bound` はべき反復を使用して推定されます。
