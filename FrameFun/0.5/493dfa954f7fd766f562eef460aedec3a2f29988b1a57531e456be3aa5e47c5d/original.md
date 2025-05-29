```
abstract type ProjectionStyle <: SamplingStyle end
```

The sampling operator corresponds to projections (using inner products). The kind of inner product is specified by [`GramStyle`](@ref), [`DiscreteGramStyle`](@ref), [`RectangularGramStyle`](@ref)
