```
signal = Var(; kwargs...)::OrderedDict{Symbol,Any}
```

Returns a *variable* signal definition in form of a dictionary. `kwargs...` are key/value pairs of variable attributes.

The *:values* key represents a *signal array* of any element type  as function of the independent signal(s) (or is the k-th independent variable). A *signal array* has indices `[i1,i2,...,j1,j2,...]` to hold variable elements `[j1,j2,...]`  at the `[i1,i2,...]` independent signal(s). If an element of a signal array is *not defined*  it has a value of *missing*. Furthermore, additional attributes can be stored. 

The following keys are recognized (all are *optional* with exception of *:values* that must be either directly defined or via :alias):

| key              | value (of type String, if not obvious from context)                                                                                                                                                                                                   |
|:---------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `:values`        | Array{T,N}: `signal[:values][i1,i2,...j1,j2,...]` is value `[j1,j2,...]` at the `[i1,i2,...]` independent signal(s), or `signal[:values][i_k]` is value `[i_k]` of the k-th independent variable.                                                     |
| `:unit`          | String: Unit of all signal elements (parseable with `Unitful.uparse`), e.g., `"kg*m*s^2"`. Array{String,N}: `signal[:unit][j1,j2,...]` is unit of variable element `[j1,j2,...]`.                                                                     |
| `:info`          | Short description of signal (= `description` of [FMI 3.0](https://fmi-standard.org/docs/3.0/) and of [Modelica](https://specification.modelica.org/maint/3.5/MLS.html)).                                                                              |
| `:independent`   | = true, if independent variable (k-th independent variable is k-th Var insignal table)                                                                                                                                                                |
| `:variability`   | `"continuous", "clocked", "clock", "discrete",` or `"tunable"` (parameter).                                                                                                                                                                           |
| `:state`         | = true, if signal is a (*continuous*, *clocked*, or *discrete*) state.                                                                                                                                                                                |
| `:der`           | String: [`getSignal`](@ref)`(signalTable, signal[:der])[:values]` is the *derivative* of `signal[:values]`.                                                                                                                                           |
| `:clock`         | String: [`getSignal`](@ref)`(signalTable, signal[:clock])[:values]` is the *clock* associated with `signal[:values]` (is only defined at clock ticks and otherwise is *missing*). If `Vector{String}`, a set of clocks is associated with the signal. |
| `:alias`         | String: `signal[:values]` is a *reference* to [`getSignal`](@ref)`(signalTable, signal[:alias])[:values]`. The *reference* is set and attributes are merged when the Var-signal is added to the signal table.                                         |
| `:interpolation` | Interpolation of signal points (`"linear", "none"`). If not provided, `interpolation` is deduced from `:variability` and otherwise interpolation is `"linear".                                                                                        |
| `:extrapolation` | Extrapolation outside the values of the independent signal (`"none"`).                                                                                                                                                                                |

Additionally, any other signal attributes can be stored in `signal` with a desired key, such as *Variable Types* of [FMI 3.0](https://fmi-standard.org/docs/3.0/#definition-of-types).

# Example

```julia
using SignalTables

t = (0.0:0.1:0.5)
t_sig = Var(values = t, unit=u"s",  independent=true)
w_sig = Var(values = sin.(t), unit="rad/s", info="Motor angular velocity")
c_sig = Var(values = [1.0, missing, missing, 4.0, missing, missing],
            variability="clocked")
b_sig = Var(values = [false, true, true, false, false, true])
a_sig = Var(alias = "w_sig")
```
