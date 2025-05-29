```
StepTimer(; kwargs...)
```

Collect time stamps every $N$ steps to measure the compute time per time step and write it to a [JSON](https://en.wikipedia.org/wiki/JSON) file.

# Keywords

  * `path = "output/timestamps.json"`: The path to the output file.
  * `frequency = 1`: The number of time steps $N$ computed between each collected time stamp.
