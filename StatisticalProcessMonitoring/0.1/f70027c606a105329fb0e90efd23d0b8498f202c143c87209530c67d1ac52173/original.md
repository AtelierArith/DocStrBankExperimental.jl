```
QRL(value, qtl)
```

Value of the in-control quantile of the run length of the control chart, i.e. if $RL = \inf\{t > 0 : \text{Chart detects OC}\}$ is the run length, then `value` is the value of the `qtl`-level quantile of the distribution of $RL$ if the process is in-control.

### Arguments

  * `value::Float64`: The nominal value of the run length quantile.
  * `qtl::Float64`: The level of the quantile, must be between 0 and 1. Default is 0.5.
