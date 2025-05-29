```
kfilter_full_sample!(settings::KalmanSettings, status::SizedKalmanStatus)
```

Run Kalman filter from `t=1` to `history_length` and update `status` in-place.
