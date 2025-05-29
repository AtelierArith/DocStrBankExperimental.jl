```
Job(command::Base.AbstractCmd; stdout=nothing, stderr=nothing, append::Bool=false, kwargs...)
Job(f::Function; kwargs...)
Job(task::Task; kwargs...)
```

# Arguments

  * `command::Base.AbstractCmd`: the command to run.
  * `f::Function`: the function to run without any arguments, like `f()`.
  * `task::Task`: the task to run. Eg: `@task(1+1)`.

# Common Keyword Arguments (kwargs...)

  * `name::String = ""`: job name.
  * `user::String = ""`: user that job belongs to.
  * `ncpu::Real = 1.0`: number of CPU this job is about to use (can be `Float64`, eg: `1.5` will use 150% CPU).
  * `mem::Integer = 0`: number of memory this job is about to use (supports TB, GB, MB, KB, B=1).
  * `schedule_time::Union{DateTime,Period} = DateTime(0)`: The expected time to run.
  * `dependency`: defer job until specified jobs reach specified state (QUEUING, RUNNING, DONE, FAILED, CANCELLED, PAST). PAST is the super set of DONE, FAILED, CANCELLED, which means the job will not run in the future. Eg: `DONE => job`, `[DONE => job1; PAST => job2]`.

!!! info "Dependency"
    The default state is DONE, so `DONE => job` can be simplified to `job`.   To be compatible with old versions, you can also use job id (Int): `[DONE => job.id]`.


  * `wall_time::Period = Year(1)`: wall clock time limit. Jobs will be terminated after running for this period.
  * `priority::Int = 20`: lower means higher priority.
  * `cron::Cron = Cron(:none)`: job recurring at specfic date and time. See more at [`Cron`](@ref).
  * `until::Union{DateTime,Period} = DateTime(9999,1,1)`: stop job recurring `until` date and time.

# Experimental Keyword Arguments - Output Redirection:

  * `stdout=nothing`: redirect stdout to the file.
  * `stderr=nothing`: redirect stderr to the file.
  * `append::Bool=false`: append the stdout or stderr or not.

!!! note
    Redirecting in Julia are not thread safe, so unexpected redirection might be happen if you are running programs in different `Tasks` simultaneously (multi-threading).


See also [`submit!`](@ref), [`@submit`](@ref), [`Cron`](@ref)
