```
function simulate_magnetization(sequence, parameters)
```

Convenience function to simulate magnetization without specifying the computational resource. The function automatically selects the appropriate resource based on the type of the `sequence` and `parameters`. The fallback case is to use multi-threaded CPU computations.
