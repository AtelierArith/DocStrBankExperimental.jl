```
logpredlik(m::AbstractDPM, data, i::Int, k::Int)
```

Return the log-pdf of the `i`th response at its current value, given the other  responses, the other cluster labels, and the own cluster label fixed at `k`.  The responses should be present in `data`.
