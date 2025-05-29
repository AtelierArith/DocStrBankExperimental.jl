```
random_cycles(; periods=10 dt=π/20, σ = 0.05, frange = (0.8, 2.0))
```

Make a timeseries that is composed of `period` full sine wave periods, each with a random frequency in the range given by `frange`, and added noise with std `σ`. The sampling time is `dt`.
