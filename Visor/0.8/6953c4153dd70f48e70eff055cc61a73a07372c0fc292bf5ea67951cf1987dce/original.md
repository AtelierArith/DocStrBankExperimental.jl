```
supervise(processes::Vector{<:Supervised};
          intensity::Int=DEFAULT_INTENSITY,
          period::Int=DEFAULT_PERIOD,
          strategy::Symbol=:one_for_one,
          terminateif::Symbol=:empty,
          handler::Union{Nothing, Function}=nothing,
          wait::Bool=true)::Supervisor
```

The root supervisor start a family of supervised `processes`.

Return the root supervisor or wait for supervisor termination if `wait` is true.

# Arguments

  * `intensity::Int`: maximum number of restarts allowed in `period` seconds.
  * `period::Int`: time interval that controls the restart intensity.
  * `strategy::Symbol`: defines the restart strategy:

      * `:one_for_one`: only the terminated task is restarted.
      * `:one_for_all`: if a child task terminates, all other tasks are terminated, and then all children,                 including the terminated one, are restarted.
      * `:rest_for_one`: if a child task terminates, the rest of the children tasks (that is, the child tasks                  after the terminated process in start order) are terminated. Then the terminated                  child task and the rest of the child tasks are restarted.
      * `:one_terminate_all`: if a child task terminates then the remaining tasks will be concurrently terminated                       (the startup order is not respected).
  * `terminateif::Symbol`:

      * `:empty`: terminate the supervisor when all child tasks terminate.
      * `:shutdown`: the supervisor terminate at shutdown.
  * `handler`: a callback function with prototype `fn(process, event)` invoked when process events occurs:

when process tasks throws exception and when a process terminate because of a `ProcessFatal` reason.

  * `wait::Bool`: wait for supervised nodes termination.

```julia
    children = [process(worker, args=(15,"myid"))]
    supervise(children)
```
