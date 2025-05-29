```
kalman_filter(model::StateSpaceModel; filter::KalmanFilter=default_filter(model)) -> FilterOutput
```

モデル内の推定されたハイパーパラメータと希望する `filter` を使用してデータをフィルタリングします。
