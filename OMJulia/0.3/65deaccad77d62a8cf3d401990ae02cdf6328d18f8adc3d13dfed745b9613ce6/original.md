```
simulate(omc; resultfile=nothing, simflags="", verbose=false)
```

Simulate modelica model.

## Arguments

  * `omc::OMCSession`:        OpenModelica compiler session, see `OMCSession()`.

## Keyword Arguments

  * `resultFile::Union{String, Nothing}`: Result file to write simulation results into.
  * `simflags::String`:                   Simulation flags, see [Simulation Runtime Flags](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/simulationflags.html).
  * `verbose::Bool`:                      [debug] Log cmd call to `log.txt` and `error.txt`.

## Examples

```julia
simulate(omc)
```

Specify result file:

```julia
simulate(omc, resultfile="tmpresult.mat")
```

Set simulation runtime flags:

```julia
simulate(omc, simflags="-noEmitEvent -override=e=0.3,g=9.3")
```
