```
set_runtime(; 
    # keyword arguments
    iterations::I, 
    write_interval::I, 
    time_step::N
    ) where {I<:Integer,N<:Number} = begin
    
    # returned `NamedTuple`
        (
        iterations=iterations, 
        dt=time_step, 
        write_interval=write_interval)
end
```

This is a convenience function to set the top-level runtime information. The inputs are all keyword arguments and provide basic information to flow solvers just before running a simulation.

# Input arguments

  * `iterations::Integer` specifies the number of iterations in a simulation run.
  * `write_interval::Integer` defines how often simulation results are written to file (on the current working directory). The interval is currently based on number of iterations. Set to `-1` to run without writing results to file.
  * `time_step::Number` the time step to use in the simulation. Notice that for steady solvers this is simply a counter and it is recommended to simply use `1`.

# Example

```julia
runtime = set_runtime(
    iterations=2000, time_step=1, write_interval=2000)
```
