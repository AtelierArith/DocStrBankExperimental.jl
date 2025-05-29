```
abstract type Triangulation{Dt,Dp}
```

A discredited physical domain associated with a `DiscreteModel{Dm,Dp}`.

`Dt` and `Dm` can be different.

The (mandatory) `Triangulation` interface can be tested with

  * [`test_triangulation`](@ref)
