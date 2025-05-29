```julia
struct Hold <: Symbolics.Operator
```

Represents a hold operator. A continuous-time signal is produced by holding a discrete-time signal `x` with zero-order hold.

```
cont_x = Hold()(disc_x)
```
