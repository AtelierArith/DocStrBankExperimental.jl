```
PolarForm{T, IT, VT, MT} <: AbstractPolarFormulation
```

Implement the polar formulation associated to the network's equations.

Wrap a [`PS.PowerNetwork`](@ref) network to load the data on the target device (`CPU()` and `CUDABackend()` are currently supported).

## Example

```jldoctest; setup=:(using ExaPF)
julia> const PS = ExaPF.PowerSystem;

julia> network_data = PS.load_case("case9.m");

julia> polar = PolarForm(network_data, ExaPF.CPU())
Polar formulation (instantiated on device CPU(false))
Network characteristics:
    #buses:      9  (#slack: 1  #PV: 2  #PQ: 6)
    #generators: 3
    #lines:      9
giving a mathematical formulation with:
    #controls:   5
    #states  :   14

```
