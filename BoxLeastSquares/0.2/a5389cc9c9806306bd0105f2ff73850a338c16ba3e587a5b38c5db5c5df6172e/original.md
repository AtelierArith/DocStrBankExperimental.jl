```
autoperiod(t, duration;
    minimum_n_transit=3, frequency_factor=1.0,
    [minimum_period, maximum_period])
```

Automatically determine a period grid from the given times and duration(s). Periods are selected such that at least `minimum_n_trasnit` transits occur. The default minimum period is twice the maximum duration. The default maximum period is `(maximum(t) - minimum(t)) / (minimum_n_transit - 1)`. The frequency factor changes the granularity in frequency space- a smaller frequency factor will create a finer period grid.
