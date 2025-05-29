```
kalman_smoother(model::StateSpaceModel; filter::KalmanFilter=default_filter(model)) -> FilterOutput
```

Apply smoother to data filtered by `filter` and the estimated hyperparameters in `model`.
