```
kalman_smoother(model::StateSpaceModel; filter::KalmanFilter=default_filter(model)) -> FilterOutput
```

フィルターによってフィルタリングされたデータとモデル内の推定ハイパーパラメータにスムーザーを適用します。
