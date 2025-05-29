```
struct TaskOutput <: QuEraSchema
```

The result of executing a `QuEraTaskSpecification` on the machine.

Output of [`execute`](@ref) function.

# Fields

  * `task_status_code::Int`: Task Status
  * `shot_outputs::Vector{ShotOutput}`: Contains pre- and post- shot

sequence in binary of if atoms are in Rydberg/Ground state.
