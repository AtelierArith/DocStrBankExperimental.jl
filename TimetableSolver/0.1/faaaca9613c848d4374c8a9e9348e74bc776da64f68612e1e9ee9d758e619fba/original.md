```
solve!(schedule::Schedule, timeout::Float64 = Inf, all_solutions::Bool = false)::Tuple{OrderedDict{String,String},MOI.TerminationStatusCode}
```

Solve a given schedule in place and return a `String=>String` solution and status code.

# Arguments

  * `schedule::Schedule`: Schedule object representing the problem.
  * `timeout::Float64=Inf`: Float representing the maximum time to run the model.
  * `all_solutions::Bool=false`: Bool representing whether to return all solutions or just the first.

# Notes

  * Schedule is optimally solved only if the status code is [`MOI.OPTIMAL`](https://jump.dev/JuMP.jl/stable/moi/reference/models/#MathOptInterface.TerminationStatusCode).
