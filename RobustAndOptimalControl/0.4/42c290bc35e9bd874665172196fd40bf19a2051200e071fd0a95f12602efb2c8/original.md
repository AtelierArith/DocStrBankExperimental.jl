```
splitter(u::Symbol, n::Int, timeevol = Continuous())
```

Return a named system that splits an input signal into `n` signals. This is useful when an external signal entering a block diagram is to be connected to multiple inputs. See the tutorial  https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/hinf_connection/ for example usage. An alternative way of connecting an external input to several input ports with the same name is to pass `connect(..., unique=false)`.

# Arguments:

  * `u`: Named of the signal to split
  * `n`: Number of splits
