```
Predictive(prediction_data)
```

監視学習タスクのための予測戦略であり、モデルが提供された入力特徴のセット（`prediction_data`）に基づいてラベルを予測します。

# パラメータ

  * `prediction_data`: 予測に使用される入力データ、`feature` x `sample`

# 説明

`Predictive`予測メソッドは、提供された入力データ（`prediction_data`）を使用して、モデル内の学習された関係に基づいて対応するラベルまたは出力を生成します。
