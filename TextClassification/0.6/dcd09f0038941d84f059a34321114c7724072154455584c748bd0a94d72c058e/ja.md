```
precision_score(gold, predicted; weight=:macro)::Float64
```

これは、ゴールドデータセットと予測リスト `predict` の間の精度を計算します。

バイナリおよびマルチクラスの問題に対して、希望する重み付けスキームを適用します。

  * `:macro` は各クラスに均等な重みを適用します
  * `:weigthed` 各クラスの重みはゴールドにおけるその人口に比例します
  * `:micro` はクラスを区別せずに全体の精度を返します
