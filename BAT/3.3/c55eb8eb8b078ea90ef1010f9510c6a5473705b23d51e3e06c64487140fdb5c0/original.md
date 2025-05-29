```
struct HierarchicalDistribution <: ContinuousDistribution
```

*Experimental feature, not part of stable public API.*

A hierarchical distribution, useful for hierarchical models/priors.

Constructors:

  * `HierarchicalDistribution(f::Function, primary_dist::NamedTupleDist)`

with a functon `f` that returns a `ContinuousDistribution` for any variate `v` drawn from `primary_dist`.

Example:

```julia
hd = HierarchicalDistribution(
    v -> NamedTupleDist(
        baz = fill(Normal(v.bar, v.foo), 3)
    ),
    NamedTupleDist(
        foo = Exponential(3.5),
        bar = Normal(2.0, 1.0)
    )
)

varshape(hd) == NamedTupleShape(
    foo = ScalarShape{Real}(),
    bar = ScalarShape{Real}(),
    baz = ArrayShape{Real}(3)
)

v = rand(hd)
```

!!! note
    All fields of `HierarchicalDistribution` are considered internal and subject to change without deprecation.

