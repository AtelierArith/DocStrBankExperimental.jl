```
Job(core::Thunk; description="", username="")
```

Create a simple job.

# Arguments

  * `core`: a `Thunk` that encloses the job core definition.
  * `name`: give a short name to the job.
  * `description::String=""`: describe what the job does in more detail.
  * `username::String=""`: indicate who executes the job.

# Examples

```jldoctest
julia> using Thinkers

julia> a = Job(Thunk(sleep, 5); username="me", description="Sleep for 5 seconds");

julia> b = Job(Thunk(run, `pwd` & `ls`); username="me", description="Run some commands");
```
