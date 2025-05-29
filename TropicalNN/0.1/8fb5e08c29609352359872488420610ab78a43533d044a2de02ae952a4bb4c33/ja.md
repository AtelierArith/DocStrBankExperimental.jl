```
mlp_to_trop_with_strong_elim(linear_maps, bias, thresholds) は、多層パーセプトロンに関連する熱帯プイセウス有理関数を計算し、各層で冗長な単項式を削除するために monomial_strong_elim を実行します。

inputs: linear maps: ニューラルネットワークの重み行列を含む配列。
        bias: 各層のバイアスを含む配列
        thresholds: 各層の活性化関数の閾値を含む配列、すなわち活性化が
        形式 x => max(x,t) であるための t の値。
outputs: TropicalPuiseuxRational 型のオブジェクト。
```
