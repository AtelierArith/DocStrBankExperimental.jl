```
MultichannelComponent <: AbstractComponent
```

Projects a `AbstractComponent` to multiple "channels" via the `projection` vector.

Optionally, `noise` can be added to the source prior to projection. By default a `MultichannelComponent` can be constructed using one of the following options for `projection`:

  * `projection::AbstractVector`: Directly pass a custom projection vector.
  * `projection::Pair{<:AbstractHeadmodel,String}`: Generate a projection vector by specifying which headmodel to use and which sources should be active.

# Fields

  * `component::AbstractComponent`: The component that should be projected to the sensors.
  * `projection::AbstractVector` or `projection::Pair{<:AbstractHeadmodel,String}`: Vector `p` that projects the (source) component `c[t]` (where `t` is time) to the sensors `s`.   The length of `p` equals the number of sensors `s`. Typically, it is a slice of the leadfield matrix. `out[s,t] = p[s]*c[t]`.
  * `noise::AbstractNoise` (optional): Noise added in the source space. Default is `NoNoise`.

# Examples

```julia-repl
# Variant 1: Specify the projection vector manually
julia> c1 = LinearModelComponent(; basis = p100(), formula = @formula(0 ~ 1), β = [1]);

julia> mc1 = UnfoldSim.MultichannelComponent(c, [1, 2, -1, 3, 5, 2.3, 1])
MultichannelComponent
  component: LinearModelComponent
  projection: Array{Float64}((7,)) [1.0, 2.0, -1.0, 3.0, 5.0, 2.3, 1.0]
  noise: NoNoise NoNoise()

# Variant 2: Use a headmodel and specify a source
julia> c2 = LinearModelComponent(; basis = p300(), formula = @formula(0 ~ 1), β = [1]);

julia> hart = headmodel(type = "hartmut");
Please cite: HArtMuT: Harmening Nils, Klug Marius, Gramann Klaus and Miklody Daniel - 10.1088/1741-2552/aca8ce

julia> mc2 = UnfoldSim.MultichannelComponent(c2, hart => "Right Occipital Pole")
MultichannelComponent
  component: LinearModelComponent
  projection: Array{Float64}((227,)) [-0.03461859471337842, -0.04321094803502425, 0.0037088347968313525, -0.014722528968861278, -0.0234889834534478, 0.02731807504242923, 0.038863688452528036, 0.1190531258070562, -0.09956890221613562, -0.0867729334438599  …  0.37435404409695094, -0.020863789022627935, 0.25627478723535513, -0.05777985212119245, 0.37104376432271147, -0.19446620423767172, 0.2590764703721097, -0.12923837607416555, 0.1732886690359311, 0.4703016561960567]
  noise: NoNoise NoNoise()
```

See also [`LinearModelComponent`](@ref), [`MixedModelComponent`](@ref).
