```
AliveCallback(analysis_interval=0, alive_interval=analysis_interval÷10)
```

Inexpensive callback showing that a simulation is still running by printing some information such as the current time to the screen every `alive_interval` time steps. If `analysis_interval ≂̸ 0`, the output is omitted every `analysis_interval` time steps.
