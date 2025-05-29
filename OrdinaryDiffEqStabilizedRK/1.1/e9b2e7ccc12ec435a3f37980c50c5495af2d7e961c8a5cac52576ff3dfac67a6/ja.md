Assyr Abdulle, Alexei A. Medovikov. Second Order Chebyshev Methods based on Orthogonal Polynomials. Numerische Mathematik, 90 (1), pp 1-18, 2001. doi: https://dx.doi.org/10.1007/s002110100292

ROCK2: 安定化された明示法。第二次安定化ルンゲ-クッタ法。実固有値に対して高い安定性を示し、中程度の大きさの複素固有値を許容するように滑らかにされています。

この方法は、オプションのキーワード引数 `min_stages`、`max_stages`、および `eigen_est` を取ります。関数 `eigen_est` は次の形式である必要があります。

`eigen_est = (integrator) -> integrator.eigen_est = upper_bound`、

ここで `upper_bound` はヤコビ行列のスペクトル半径の推定上限です。`eigen_est` が提供されない場合、`upper_bound` はべき反復を使用して推定されます。
