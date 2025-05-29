```
all_queue()
all_queue(id::Integer)
all_queue(state::Symbol)
all_queue(needle::Union{AbstractString,AbstractPattern,AbstractChar})
```

  * `state::Symbol`: get jobs with a specific state, including `:all`, `QUEUING`, `RUNNING`, `DONE`, `FAILED`, `CANCELLED`, `PAST`.

    > `PAST` is the superset of `DONE`, `FAILED`, `CANCELLED`.
  * `needle::Union{AbstractString,AbstractPattern,AbstractChar}`: get jobs if they contain `needle` in their name or user.
  * `id::Integer`: get the job with the specific `id`.
