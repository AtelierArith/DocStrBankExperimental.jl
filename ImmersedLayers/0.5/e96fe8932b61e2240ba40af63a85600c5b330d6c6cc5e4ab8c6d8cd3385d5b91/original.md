```
@scalarsurfacemetric(name)
```

A function that returns a time-varying scalar surface metric should have the signature `name(state,constraint,sys::ILMSystem,t,bodyid,[,kwargs...])`, where `state` is a solution vector (of the same type as returned by `state(zeros_sol(sys))`), `constraint` is of the same type as returned by `constraint(zeros_sol(sys))`), `sys` is the system struct, `t` is time, `bodyid` is the body ID, and `kwargs` are any additional keyword arguments. This macro extends that function so that it will also operate on the integrator e.g, `name(integrator,bodyid)`, and the solution history array `sol`, e.g., `name(sol::ODESolution,sys,t,bodyid)`, using interpolation for values of `t` that are not explicitly in the solution array. It can also take a range of values of `t`, e.g, `name(sol::ODESolution,sys,0.1:0.01:0.2,bodyid)`. And finally, it can simply take `name(sol::ODESolution,sys,bodyid)` to return the entire history.
