```
LinModel(sys::DelayLtiSystem, Ts; i_u=1:size(sys,2), i_d=Int[])
```

Discretize with zero-order hold when `sys` is a continuous system with delays.

The delays must be multiples of the sample time `Ts`.
