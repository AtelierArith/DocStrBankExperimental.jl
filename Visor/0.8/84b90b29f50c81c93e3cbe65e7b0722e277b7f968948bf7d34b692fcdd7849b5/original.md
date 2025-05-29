```
supervisor(
    id, processes;
    intensity=DEFAULT_INTENSITY,
    period=DEFAULT_PERIOD,
    strategy=:one_for_one,
    terminateif=:empty)::SupervisorSpec
```

Declare a supervisor of one or more `processes`.

`processes` may be a `Process` or an array of `Process`.

```jldoctest
julia> using Visor

julia> mytask(pd) = ();

julia> supervisor("mysupervisor", process(mytask))
mysupervisor
```

```jldoctest julia> using Visor

julia> tsk1(pd) = ();

julia> tsk2(pd) = ();

julia> supervisor("mysupervisor", [process(tsk1), process(tsk2)]) mysupervisor

See [Supervisor](@ref) documentation for more details.
