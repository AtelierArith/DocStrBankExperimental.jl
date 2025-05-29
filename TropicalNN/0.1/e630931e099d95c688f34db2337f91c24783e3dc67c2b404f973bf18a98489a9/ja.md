```
mlp_to_trop_with_quicksum_with_strong_elim(linear_maps, bias, thresholds) は、マルチレイヤパーセプトロンに関連する熱帯プイセウス有理関数を計算します。各層で monomial_strong_elim を実行し、熱帯オブジェクトのために quicksum 操作を使用します。

inputs: linear maps: ニューラルネットワークの重み行列を含む配列。
        bias: 各層のバイアスを含む配列
        thresholds: 各層の活性化関数の閾値を含む配列、すなわち活性化が
        形式 x => max(x,t) であるための t の値。
outputs: TropicalPuiseuxRational 型のオブジェクト。
```
