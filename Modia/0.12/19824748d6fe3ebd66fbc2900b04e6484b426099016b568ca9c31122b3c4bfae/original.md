```
signal    = get_result(instantiatedModel, name; unit=true)
dataFrame = get_result(instantiatedModel; onlyStates=false, extraNames=missing)
```

  * First form: After a successful simulation of `instantiatedModel`, return the result for the signal `name::String` as vector of points together with its unit. The time vector has path name `"time"`. If `unit=false`, the signal is returned, **without unit**.
  * Second form: Return the **complete result** in form of a DataFrame object. Therefore, the whole functionality of package [DataFrames](https://dataframes.juliadata.org/stable/) can be used, including storing the result on file in different formats. Only scalar Var(..) variables are included in the DataFrame object. If `onlyStates=true`, then only the states and the signals identified with `extraNames::Vector{String}` are stored in `dataFrame`. If `onlyStates=false` and `extraNames` given, then only the signals identified with `extraNames` are stored in `dataFrame`.

# Example

```julia
using Modia
@usingModiaPlot
using Unitful

include("$(Modia.path)/examples/Pendulum.jl")
using  .Model_Pendulum

pendulum = simulationModel(Pendulum)
simulate!(pendulum, stopTime=7.0)

# Get one signal from the result and plot with the desired plot package
time = get_result(pendulum, "time")  # vector with unit u"s"
phi  = get_result(pendulum, "phi")   # vector with unit u"rad"

import PyPlot
PyPlot.figure(4)   # Change to figure 4 (or create it, if it does not exist)
PyPlot.clf()       # Clear current figure
PyPlot.plot(stripUnit(time), stripUnit(phi), "b--", label="phi in " * string(unit(phi[1])))
PyPlot.xlabel("time in " * string(unit(time[1])))
PyPlot.legend()

# Get complete result and plot one signal
result = get_result(pendulum)
plot(result, "phi")

# Get only states to be used as reference and compare result with reference
reference = get_result(pendulum, onlyStates=true)
(success, diff, diff_names, max_error, within_tolerance) =
    SignalTables.compareResults(result, reference, tolerance=0.01)
println("Check results: success = success")
```
