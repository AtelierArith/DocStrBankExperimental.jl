```
ConfigSampler{N,S,C} <: AbstractSetNumber
ConfigSampler(elements::StaticElementVector)
```

The algebra for sampling one configuration, where `N` is the length of configurations, `C` is the size of storage in unit of `UInt64`, `S` is the bit width to store a single element in a configuration, i.e. `log2(# of flavors)`, for bitstrings, it is `1``.

!!! note
    `ConfigSampler` is a **probabilistic** commutative semiring, adding two config samplers do not give you deterministic results.


## Fields

  * `data` is a [`StaticElementVector`](@ref) as the sampled solution.

## Examples

```jldoctest; setup=:(using GenericTensorNetworks, Random; Random.seed!(2))
julia> ConfigSampler(StaticBitVector([1,1,1,0,0]))
ConfigSampler{5, 1, 1}(11100)

julia> ConfigSampler(StaticBitVector([1,1,1,0,0])) + ConfigSampler(StaticBitVector([1,0,1,0,0]))
ConfigSampler{5, 1, 1}(10100)

julia> ConfigSampler(StaticBitVector([1,1,1,0,0])) * ConfigSampler(StaticBitVector([0,0,0,0,1]))
ConfigSampler{5, 1, 1}(11101)

julia> one(ConfigSampler{5, 1, 1})
ConfigSampler{5, 1, 1}(00000)

julia> zero(ConfigSampler{5, 1, 1})
ConfigSampler{5, 1, 1}(11111)
```
