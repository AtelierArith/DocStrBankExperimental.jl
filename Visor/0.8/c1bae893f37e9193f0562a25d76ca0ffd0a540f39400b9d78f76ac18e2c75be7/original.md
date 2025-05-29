```
supervise(proc::Supervised;
          intensity::Int=DEFAULT_INTENSITY,
          period::Int=DEFAULT_PERIOD,
          strategy::Symbol=:one_for_one,
          terminateif::Symbol=:empty,
          handler::Union{Nothing, Function}=nothing,
          wait::Bool=true)::Supervisor
```

The root supervisor start a supervised process defined by `proc`.
