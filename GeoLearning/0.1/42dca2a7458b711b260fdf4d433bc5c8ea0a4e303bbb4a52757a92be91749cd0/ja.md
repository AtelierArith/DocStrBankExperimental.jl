```
PointwiseLearn(model)
```

地理空間データを各ポイントの特徴（および可能であればラベル）を持つ表形式に変換し、その後、古典的な統計学習 `model` を用いて問題を解決する学習ソルバーです。

## パラメータ

  * `model` - `MLJModelInterface.jl` を実装した学習モデル。

## 参考文献

  * Hoffimann et al. 2020. [Geostatistical Learning: Challenges and Opportunities](https://arxiv.org/abs/2102.08791)
