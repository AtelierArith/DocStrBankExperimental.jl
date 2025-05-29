```julia
wait(run::XRT.XRTWrap.Run) -> XRT.XRTWrap.ErtCmdState.Type

```

Wait for a given [`Run`](@ref) object to complete execution. The method will return as soon as the execution is completed.
