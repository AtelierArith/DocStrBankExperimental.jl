```
frequencyspec(r::R; logscale=true)
```

Generate `RheoFreqData` struct with only the frequency data distributed on a linear or log scale.

# Arguments

  * `r`: range, e.g. 1:0.1:100
  * `logscale`: if true, set the range in logscale, e.g. -2:0.1:20  –> 10 values per decade between 10^-2 and 10^2
