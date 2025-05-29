`SciML.ReturnCode`

`SciML.ReturnCode` is the standard return code enum interface for the SciML interface. Return codes are notes given by the solvers to indicate the state of the solution, for example whether it successfully solved the equations, whether it failed to solve the equations, and importantly, why it exited.

## Using `SciML.ReturnCode`

`SciML.ReturnCode` use the interface of [EnumX.jl](https://github.com/fredrikekre/EnumX.jl) and thus inherits all of the behaviors of being an EnumX. This includes the Enum type itself being referred to as `SciML.ReturnCode.T`, and each of the constituent enum states being referred to via `getproperty`, i.e. `SciML.ReturnCode.Success`.

## Note About Success Checking

Previous iterations of the interface suggested using `sol.retcode == :Success`, however, that is now not advised instead should be replaced with `SciMLBase.successful_retcode(sol)`. The reason is that there are many different codes that can be interpreted as successful, such as `ReturnCode.Terminated` which means successfully used `terminate!(integrator)` to end an integration at a user-specified condition. As such, `successful_retcode` is the most general way to query for if the solver did not error.

## Properties

  * `successful_retcode(retcode::ReturnCode.T)`: Determines whether the output enum is considered a success state of the solver, i.e. the solver successfully solved the equations. `ReturnCode.Success` is the most basic form, simply declaring that it was successful, but many more informative success return codes exist as well.
