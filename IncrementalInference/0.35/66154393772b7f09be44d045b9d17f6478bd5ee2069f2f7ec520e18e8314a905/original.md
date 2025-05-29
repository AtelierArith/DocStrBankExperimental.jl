```julia
struct Mixture{N, F<:DistributedFactorGraphs.AbstractFactor, S, T<:Tuple} <: DistributedFactorGraphs.AbstractFactor
```

A `Mixture` object for use with either a `<: AbstractPrior` or `<: AbstractRelative`.

Notes

  * The internal data representation is a `::NamedTuple`, which allows total type-stability for all component types.
  * Various construction helpers can accept a variety of inputs, including `<: AbstractArray` and `Tuple`.
  * `N` is the number of components used to make the mixture, so two bumps from two Normal components means `N=2`.

DevNotes

  * FIXME swap API order so Mixture of distibutions works like a distribtion, see Caesar.jl #808

      * Should not have field mechanics.
  * TODO on sampling see #1099 and #1094 and #1069

Example

```juila
# prior factor
msp = Mixture(Prior, 
              [Normal(0,0.1), Uniform(-pi/1,pi/2)],
              [0.5;0.5])

addFactor!(fg, [:head], msp, tags=[:MAGNETOMETER;])

# Or relative
mlr = Mixture(LinearRelative, 
              (correlator=AliasingScalarSampler(...), naive=Normal(0.5,5), lucky=Uniform(0,10)),
              [0.5;0.4;0.1])

addFactor!(fg, [:x0;:x1], mlr)
```
