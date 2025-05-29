```julia
queue(; all::Bool = false)    -> Vector{Job}
queue(state::Symbol )         -> Vector{Job}
queue(needle)                 -> Vector{Job}
queue(state::Symbol , needle) -> Vector{Job}
queue(needle, state::Symbol ) -> Vector{Job}
queue(id::Integer)            -> Job
```

  * `all::Bool`: if true, get all jobs. if false, get only running and queuing jobs.
  * `state::Symbol`: get jobs with a specific state, including `:all`, `QUEUING`, `RUNNING`, `DONE`, `FAILED`, `CANCELLED`, `PAST`.

    > `PAST` is the superset of `DONE`, `FAILED`, `CANCELLED`.
  * `needle::Union{AbstractString,AbstractPattern,AbstractChar}`: get jobs if they contain `needle` in their name or user.
  * `id::Integer`: get the job with the specific `id`.
