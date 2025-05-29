function which returns the linearize model of modelica model, The function returns four matrices A, B, C, D

```
linearize(omc; lintime = nothing, simflags= nothing, verbose=true)
```

## Arguments

  * `omc::OMCSession`:        OpenModelica compiler session.

## Keyword Arguments

  * `lintime` : Value specifies a time where the linearization of the model should be performed
  * `simflags`: Simulation flags, see [Simulation Runtime Flags](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/simulationflags.html).

## Examples of using linearize() API

```julia
linearize(omc)
```

Specify result file:

```julia
linearize(omc, lintime="0.5")
```

Set simulation runtime flags:

```julia
linearize(omc, simflags="-noEmitEvent")
```
