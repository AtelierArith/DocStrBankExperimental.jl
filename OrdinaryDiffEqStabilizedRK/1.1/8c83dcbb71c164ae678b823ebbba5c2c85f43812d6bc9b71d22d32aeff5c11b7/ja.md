```
ROCK4(; min_stages = 0, max_stages = 152, eigen_est = nothing)
```

アッシル・アブデュレ。再帰関係を用いた四次チェビシェフ法。2002年産業応用数学会科学計算ジャーナル、23(6)、pp 2041-2054、2001年。doi: https://doi.org/10.1137/S1064827500379549

ROCK4: 安定化された明示法。四次安定化ルンゲ・クッタ法。実固有値に対して高い安定性を示し、中程度の大きさの複素固有値を許容するように滑らかにされています。

このメソッドは、オプションのキーワード引数 `min_stages`、`max_stages`、および `eigen_est` を取ります。関数 `eigen_est` は次の形式である必要があります。

`eigen_est = (integrator) -> integrator.eigen_est = upper_bound`、

ここで `upper_bound` はヤコビ行列のスペクトル半径の推定上限です。`eigen_est` が提供されていない場合、`upper_bound` はべき反復を使用して推定されます。
