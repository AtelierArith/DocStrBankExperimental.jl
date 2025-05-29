```
SolverStepClock
```

A clock that ticks at each solver step (sometimes referred to as "continuous sample time"). This clock **does generally not have equidistant tick intervals**, instead, the tick interval depends on the adaptive step-size selection of the continuous solver, as well as any continuous event handling. If adaptivity of the solver is turned off and there are no continuous events, the tick interval will be given by the fixed solver time step `dt`.

Due to possibly non-equidistant tick intervals, this clock should typically not be used with discrete-time systems that assume a fixed sample time, such as PID controllers and digital filters.
