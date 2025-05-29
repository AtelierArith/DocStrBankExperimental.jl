```julia
struct DiscreteEvent{Tcb, Tl, Tf, Td} <: BifurcationKit.AbstractDiscreteEvent
```

Structure to pass a DiscreteEvent function to the continuation algorithm. A discrete call back returns a discrete value and we seek when it changes.

  * `nb::Int64`: number of events, ie the length of the result returned by the callback function
  * `condition::Any`: = `(iter, state) -> NTuple{nb, Int64}` callback function which at each continuation state, returns a tuple. For example, to detect a value change.
  * `computeEigenElements::Bool`: whether the event requires to compute eigen elements
  * `labels::Any`: Labels used to display information. For example `labels[1]` is used to qualify an event occurring in the first component. You can use `labels = ("hopf",)` or `labels = ("hopf", "fold")`. You must have `labels::Union{Nothing, NTuple{N, String}}`.
  * `finaliser::Any`: Finaliser function
  * `data::Any`: Place to store some personal data
