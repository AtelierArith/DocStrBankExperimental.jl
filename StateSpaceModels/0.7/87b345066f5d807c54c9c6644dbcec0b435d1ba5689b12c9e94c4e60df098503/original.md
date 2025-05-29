```
kalman_filter(model::StateSpaceModel; filter::KalmanFilter=default_filter(model)) -> FilterOutput
```

Filter the data using the desired `filter` and the estimated hyperparameters in `model`.
