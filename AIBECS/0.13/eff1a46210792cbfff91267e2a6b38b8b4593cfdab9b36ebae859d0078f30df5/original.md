```
AbstractParameters{T} <: AbstractVector{T}
```

An abstract type for AIBECS model parameters.

Parameters in AIBECS use the following convenience packages:

  * Parameters
  * FieldMetadata
  * FieldDefaults
  * Flatten
  * Unitful
  * DataFrames
  * Distributions

These aim to allow for some nice features, which include

  * nice syntax for unpacking parameters in functions via the `@unpack` macro (fron UnPack.jl)
  * additional metadata on parameters
  * easy conversion to and from vectors
  * use of units and automatic conversions if necessary
  * pretty table-format displays
  * loading and saving to and from CSV files
  * prior estimates for bayesian inference and optimization

See the list of examples to get an idea of how to generate parameters for your model.

# Examples

Generate a simple parameter type via

```jldoctest
julia> struct SimpleParams{T} <: AbstractParameters{T}
           α::T
           β::T
           γ::T
       end
SimpleParams
```

To create an instance of the `SimpleParams(Float64)` type, you can do

```jldoctest
julia> p = SimpleParams(1.0, 2.0, 3.0)
SimpleParams{Float64}
│ Row │ Symbol │ Value   │
│     │ Symbol │ Float64 │
├─────┼────────┼─────────┤
│ 1   │ α      │ 1.0     │
│ 2   │ β      │ 2.0     │
│ 3   │ γ      │ 3.0     │
```

One of the core features from Parameters is unpacking in functions, e.g.,

```jldoctest
julia> function simplef(p)
           @unpack α, γ = p
           return α + γ
       end
simplef (generic function with 1 method)

julia> simplef(p) # 1.0 + 3.0
4.0
```

More complex examples are permitted by adding metadata (thanks to FieldMetadata.jl). You can add units

```jldoctest
julia> @units struct UnitParams{T} <: AbstractParameters{T}
           α::T | u"km"
           β::T | u"hr"
           γ::T | u"m/s"
       end ;

julia> p = UnitParams(1.0, 2.0, 3.0)
UnitParams{Float64}
│ Row │ Symbol │ Value   │ Unit     │
│     │ Symbol │ Float64 │ Unitful… │
├─────┼────────┼─────────┼──────────┤
│ 1   │ α      │ 1.0     │ km       │
│ 2   │ β      │ 2.0     │ hr       │
│ 3   │ γ      │ 3.0     │ m s^-1   │
```

Note that when adding units to your parameters, they will be converted to SI when unpacked, as in, e.g.,

```jldoctest
julia> function speed(p)
           @unpack α, β, γ = p
           return α / β + γ
       end
speed (generic function with 1 method)

julia> speed(p) # (1.0 km / 2.0 hr + 3 m/s) in m/s
3.138888888888889
```

Another example for optimizable/flattenable parameters

```jldoctest
julia> @initial_value @units @flattenable struct OptParams{T} <: AbstractParameters{T}
           α::T | 3.6 | u"km"  | true
           β::T | 1.0 | u"hr"  | false
           γ::T | 1.0 | u"m/s" | true
       end ;

julia> p = OptParams(initial_value(OptParams)...)
OptParams{Float64}
│ Row │ Symbol │ Value   │ Initial value │ Unit     │ Optimizable │
│     │ Symbol │ Float64 │ Float64       │ Unitful… │ Bool        │
├─────┼────────┼─────────┼───────────────┼──────────┼─────────────┤
│ 1   │ α      │ 3.6     │ 3.6           │ km       │ 1           │
│ 2   │ β      │ 1.0     │ 1.0           │ hr       │ 0           │
│ 3   │ γ      │ 1.0     │ 1.0           │ m s^-1   │ 1           │
```

Thanks to the FieldMetaData interface, you can chain the following preloaded metadata:

  * initial_value
  * units (from Unitful.jl)
  * prior (from Distributions.jl)
  * description (`String`)
  * bounds (2-element `Tuple`)
  * logscaled (`Bool`)
  * flattenable (to convert to vectors of optimizable parameters only)
  * reference (`String`)

Here is an example of parameter with all the possible metadata available in AIBECS:

```jldoctest
julia> @initial_value @units @prior @description @bounds @logscaled @flattenable @reference struct FullParams{T} <: AbstractParameters{T}
           α::T | 1.0 | u"km"  | Normal(0,1)    | "The distance"   | (-Inf, Inf) | false | false | "Jean et al., 2042"
           β::T | 2.0 | u"hr"  | LogNormal(0,1) | "The time"       | (   0, Inf) | true  | true  | "Claude et al. 1983"
           γ::T | 3.0 | u"mol" | Normal(1,2)    | "The # of moles" | (  -1,   1) | false | true  | "Dusse et al. 2000"
       end ;

julia> FullParams(4.0, 5.0, 6.0)
FullParams{Float64}
│ Row │ Symbol │ Value   │ Initial value │ Unit     │ Prior                            │ Description    │ Bounds      │ Logscaled │ Optimizable │ Reference          │
│     │ Symbol │ Float64 │ Float64       │ Unitful… │ Distribu…                        │ String         │ Tuple…      │ Bool      │ Bool        │ String             │
├─────┼────────┼─────────┼───────────────┼──────────┼──────────────────────────────────┼────────────────┼─────────────┼───────────┼─────────────┼────────────────────┤
│ 1   │ α      │ 4.0     │ 1.0           │ km       │ Normal{Float64}(μ=0.0, σ=1.0)    │ The distance   │ (-Inf, Inf) │ 0         │ 0           │ Jean et al., 2042  │
│ 2   │ β      │ 5.0     │ 2.0           │ hr       │ LogNormal{Float64}(μ=0.0, σ=1.0) │ The time       │ (0, Inf)    │ 1         │ 1           │ Claude et al. 1983 │
│ 3   │ γ      │ 6.0     │ 3.0           │ mol      │ Normal{Float64}(μ=1.0, σ=2.0)    │ The # of moles │ (-1, 1)     │ 0         │ 1           │ Dusse et al. 2000  │
```

Note that there is no check that the metadata you give is consistent. These metadata will hopefully be useful for advanced usage of AIBECS, e.g., using prior information and/or bounds for optimization.
