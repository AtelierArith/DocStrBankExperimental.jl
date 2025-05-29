```
@snapshotoutput(name)
```

A function that returns some instantaneous output about a time-varying solution should have the signature `name(state,constraint,aux_state,sys::ILMSystem,t,[args...];[kwargs...])`, where `state` is a solution vector (of the same type as returned by `state(zeros_sol(sys))`), `constraint` is of the same type as returned by `constraint(zeros_sol(sys))`), and `aux_state` is the same as `aux_state(zeros_sol(sys))`, `sys` is the system struct, `t` is time, and `args` are additional arguments and `kwargs` are any additional keyword arguments. This macro extends that function so that it will also operate on the integrator e.g, `name(integrator)`, and the solution history array `sol`, e.g., `name(sol::ODESolution,sys,t)`, using interpolation for values of `t` that are not explicitly in the solution array. It can also take a range of values of `t`, e.g, `name(sol::ODESolution,sys,0.1:0.01:0.2)`.

This will also create a function `name_xy` that operates on the same sets of arguments, but returns a spatially interpolatable version of the quantity `name`, which can be accessed with `x`, `y` coordinates. In the case of the array with a time range, it returns a vector of such interpolatable objects.
