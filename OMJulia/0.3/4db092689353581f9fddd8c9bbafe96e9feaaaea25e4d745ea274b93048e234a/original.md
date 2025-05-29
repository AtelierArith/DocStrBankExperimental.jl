```
ModelicaSystem(omc, fileName, modelName, library=nothing;
               commandLineOptions=nothing, variableFilter=nothing, customBuildDirectory=nothing)
```

Set command line options for OMCSession and build model `modelName` to prepare for a simulation.

## Arguments

  * `omc`:       OpenModelica compiler session, see `OMCSession()`.
  * `fileName`:  Path to Modelica file.
  * `modelName`: Name of Modelica model to build, including namespace if the              model is wrappen within a Modelica package.
  * `library`:   List of dependent libraries or Modelica files.              This argument can be passed as string (e.g. `"Modelica"`)              or tuple (e.g. `("Modelica", "4.0")`              or array (e.g. `["Modelica", "SystemDynamics"]`              or `[("Modelica", "4.0"), "SystemDynamics"]`).

## Keyword Arguments

  * `commandLineOptions`: OpenModelica command line options, see                       [OpenModelica Compiler Flags](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/omchelptext.html).
  * `variableFilter`:     Regex to filter variables in result file.

## Usage

```
using OMJulia
mod = OMJulia.OMCSession()
ModelicaSystem(mod, "BouncingBall.mo", "BouncingBall", ["Modelica", "SystemDynamics"], commandLineOptions="-d=newInst")
```

Providing dependent libaries:

```
using OMJulia
mod = OMJulia.OMCSession()
ModelicaSystem(mod, "BouncingBall.mo", "BouncingBall", ["Modelica", "SystemDynamics", "dcmotor.mo"])
```

See also [`OMCSession()`](@ref).
