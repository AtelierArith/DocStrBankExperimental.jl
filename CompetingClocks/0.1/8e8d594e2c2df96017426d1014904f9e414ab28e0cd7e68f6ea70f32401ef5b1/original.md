```
reset!(recorder::CommonRandomRecorder)
```

The common random recorder records the state of the random number generator for each clock, but the same clock can be enabled multiple times in one simulation, so it records the generator state for each (clock, index of the enabling of that clock). The `reset!` function says we are starting a new simulation run, so all clocks haven't been seen.
