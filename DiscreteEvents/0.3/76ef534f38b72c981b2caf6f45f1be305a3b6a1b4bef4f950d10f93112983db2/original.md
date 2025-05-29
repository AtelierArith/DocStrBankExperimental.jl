```
now!(clk::Clock, ex::A) where {A<:Action}
```

Transfer an IO-operation `ex` to `clk` or if it is a parallel clock to the master clock (on thread 1). The clock executes it before  proceeding to the next time step.
