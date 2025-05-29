```julia
struct ContinuousEvent{Tcb, Tl, T, Tf, Td} <: BifurcationKit.AbstractContinuousEvent
```

Structure to pass a ContinuousEvent function to the continuation algorithm. A continuous call back returns a **tuple/scalar** value and we seek its zeros.

  * `nb::Int64`: number of events, i.e. the length of the result returned by the callback function
  * `condition::Any`: , `(iter, state) -> NTuple{nb, T}` callback function which, at each continuation state, returns a tuple. For example, to detect crossing at 1.0 and at -2.0, you can pass `(iter, state) -> (getp(state)+2, getx(state)[1]-1)),`. Note that the type `T` should match the one of the parameter specified by the `::Lens` in `continuation`.
  * `computeEigenElements::Bool`: whether the event requires to compute eigen elements
  * `labels::Any`: Labels used to display information. For example `labels[1]` is used to qualify an event of the type `(0, 1.3213, 3.434)`. You can use `labels = ("hopf",)` or `labels = ("hopf", "fold")`. You must have `labels::Union{Nothing, NTuple{N, String}}`.
  * `tol::Any`: Tolerance on event value to declare it as true event.
  * `finaliser::Any`: Finaliser function
  * `data::Any`: Place to store some personal data
