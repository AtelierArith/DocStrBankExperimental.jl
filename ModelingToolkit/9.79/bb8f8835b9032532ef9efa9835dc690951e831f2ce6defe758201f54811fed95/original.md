```julia
struct AnalysisPoint
```

```
AnalysisPoint(input, name::Symbol, outputs::Vector)
```

Create an AnalysisPoint for linear analysis. Analysis points can be created by calling

```
connect(out, :ap_name, in...)
```

Where `out` is the output being connected to the inputs `in...`. All involved connectors (input and outputs) are required to either have an unknown named `u` or a single unknown, all of which should have the same size.

See also [`get_sensitivity`](@ref), [`get_comp_sensitivity`](@ref), [`get_looptransfer`](@ref), [`open_loop`](@ref)

# Fields

  * `input::Any`: The input to the connection. In the context of ModelingToolkitStandardLibrary.jl, this is a `RealOutput` connector.

  * `name::Symbol`: The name of the analysis point.

  * `outputs::Union{Nothing, Vector{Any}}`: The outputs of the connection. In the context of ModelingToolkitStandardLibrary.jl, these are all `RealInput` connectors.

# Example

```julia
using ModelingToolkit
using ModelingToolkitStandardLibrary.Blocks
using ModelingToolkit: t_nounits as t

@named P = FirstOrder(k = 1, T = 1)
@named C = Gain(; k = -1)
t = ModelingToolkit.get_iv(P)

eqs = [connect(P.output, C.input)
       connect(C.output, :plant_input, P.input)]
sys = ODESystem(eqs, t, systems = [P, C], name = :feedback_system)

matrices_S, _ = get_sensitivity(sys, :plant_input) # Compute the matrices of a state-space representation of the (input) sensitivity function.
matrices_T, _ = get_comp_sensitivity(sys, :plant_input)
```

Continued linear analysis and design can be performed using ControlSystemsBase.jl. Create `ControlSystemsBase.StateSpace` objects using

```julia
using ControlSystemsBase, Plots
S = ss(matrices_S...)
T = ss(matrices_T...)
bodeplot([S, T], lab = ["S" "T"])
```

The sensitivity functions obtained this way should be equivalent to the ones obtained with the code below

```julia
using ControlSystemsBase
P = tf(1.0, [1, 1])
C = 1                      # Negative feedback assumed in ControlSystems
S = sensitivity(P, C)      # or feedback(1, P*C)
T = comp_sensitivity(P, C) # or feedback(P*C)
```
