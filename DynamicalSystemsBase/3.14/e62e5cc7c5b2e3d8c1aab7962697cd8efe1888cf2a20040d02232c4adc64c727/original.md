```
observe_state(ds::DynamicalSystem, i, u = current_state(ds)) → x::Real
```

Return the state `u` of `ds` *observed* at "index" `i`. Possibilities are:

  * `i::Int` returns the `i`-th dynamic variable.
  * `i::Function` returns `f(current_state(ds))`.
  * `i::SymbolLike` returns the value of the corresponding symbolic variable.  This is valid only for dynamical systems referrencing a ModelingToolkit.jl model  which also has `i` as one of its listed variables (either uknowns or observed).  Here `i` can be anything can be anything  that could index the solution object `sol = ModelingToolkit.solve(...)`,  such as a `Num` or `Symbol` instance with the name of the symbolic variable.  In this case, a last fourth optional positional argument `t` defaults to  `current_time(ds)` and is the time to observe the state at.
  * Any symbolic expression involving variables present in the symbolic variables tracked by the system, e.g., `i = x^2 - y` with `x, y` symbolic variables.

For [`ProjectedDynamicalSystem`](@ref), this function assumes that the state of the system is the original state space state, not the projected one (this makes the most sense for allowing MTK-based indexing).

Use [`state_name`](@ref) for an accompanying name.
