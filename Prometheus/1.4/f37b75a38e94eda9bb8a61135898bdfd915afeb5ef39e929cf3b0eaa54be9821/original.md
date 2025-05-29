```
Prometheus.observe(histogram::Histogram, v::Real)
```

Add the observed value `v` to the histogram. This increases the sum and count of the histogram with `v` and `1`, respectively, and increments the counter for all buckets containing `v`.
