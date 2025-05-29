```
evolve!(comp::AbstractSource, u, t)
```

Does nothing. `u` is the value of `input` and `t` is time.

```
evolve!(comp::AbstractSink, u, t)
```

Writes `t` to time buffer `timebuf` and `u` to `databuf` of `comp`. `u` is the value of `input` and `t` is time.

```
evolve!(comp::AbstractStaticSystem, u, t)
```

Writes `u` to `buffer` of `comp` if `comp` is an `AbstractMemory`. Otherwise, `nothing` is done. `u` is the value of `input` and `t` is time. 

```
evolve!(comp::AbstractDynamicSystem, u, t)
```

Solves the differential equation of the system of `comp` for the time interval `(comp.t, t)` for the inital condition `x` where `x` is the current state of `comp` . `u` is the input function defined for `(comp.t, t)`. The `comp` is updated with the computed state and time `t`. 
