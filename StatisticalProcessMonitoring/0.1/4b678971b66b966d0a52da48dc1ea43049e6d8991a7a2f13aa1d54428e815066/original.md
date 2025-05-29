```
ARL(value)
```

Value of the in-control average run length of the control chart, i.e. if $RL = \inf\{t > 0: \text{Chart detects OC}\}$ is the run length, then the average run length $ARL$ is

$ARL = \mathbb{E}[RL|\tau = +\infty]$,

where $\{\tau = +\infty\}$ represents the process being in-control.

### Arguments

  * `value::Float64`: The nominal value of the average run length. Must be greater than 1.
