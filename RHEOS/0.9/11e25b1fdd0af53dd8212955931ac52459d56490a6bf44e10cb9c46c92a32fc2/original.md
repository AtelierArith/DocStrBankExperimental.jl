```
frequencyspec(;ω_start::Real, ω_end::Real, logstep::Real= 0.05)
```

Generate `RheoFreqData` struct with only the frequency data distributed on a log scale.

# Arguments

  * `ω_start`: min frequency
  * `ω_end`: max frequency
  * `logstep`: step between frequencies in log scale, e.g. 0.1 –> 10 values per decade.
