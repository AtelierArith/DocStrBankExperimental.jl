```
signal = Par(; kwargs...)::OrderedDict{Symbol,Any}
```

Returns a *parameter* signal definition in form of a dictionary. A parameter is a variable that is constant and is not a function of the independent variables. `kwargs...` are key/value pairs of parameter attributes.

The value of a parameter variable is stored with key *:value* in `signal` and is an instance of any Julia type (number, string, array, tuple, dictionary, ...).

The following keys are recognized (all are *optional*):

| key      | value (of type String, if not obvious from context)                                                                                                                                                         |
|:-------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `:value` | `signal[:value]` is a constant value that holds for all values of the independent signals.                                                                                                                  |
| `:unit`  | String: Unit of all signal elements (parseable with `Unitful.uparse`), e.g., `"kg*m*s^2"`. Array{String,N}: `signal[:unit][j1,j2,...]` is unit of variable element `[j1,j2,...]`.                           |
| `:info`  | Short description of signal (= `description` of [FMI 3.0](https://fmi-standard.org/docs/3.0/) and of [Modelica](https://specification.modelica.org/maint/3.5/MLS.html)).                                    |
| `:alias` | String: `signal[:value]` is a *reference* to [`getSignal`](@ref)`(signalTable, signal[:alias])[:value]`. The *reference* is set and attributes are merged when the Par-signal is added to the signal table. |

Additionally, any other signal attributes can be stored in `signal` with a desired key, such as *Variable Types* of [FMI 3.0](https://fmi-standard.org/docs/3.0/#definition-of-types).

# Example

```julia
using SignalTables

J         = Par(value = 0.02, unit=u"kg*m/s^2", info="Motor inertia")
fileNames = Par(value = ["data1.json", "data2.json"])
J_alias   = Par(alias = "J")
```
