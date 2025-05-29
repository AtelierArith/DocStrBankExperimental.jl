```
Prometheus.observe(summary::Summary, v::Real)
```

Add the observed value `v` to the summary. This increases the sum and count of the summary with `v` and `1`, respectively.
