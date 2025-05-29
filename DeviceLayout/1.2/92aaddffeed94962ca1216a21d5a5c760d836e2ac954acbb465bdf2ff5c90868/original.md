```
transform(geom::AbstractGeometry, f::Transformation)
transform(
    geom::AbstractGeometry{S};
    origin=zero(Point{S}),
    rot=0°,
    xrefl=false,
    mag=1
)
```

Return a new `AbstractGeometry` obtained by applying `f` to `geom`.

For generic `geom` and transformation, attempts to decompose `f` into a scaled isometry: `translate ∘ magnify ∘ rotate ∘ reflect_across_xaxis`. In that case, if `f` does not preserve angles, a `DomainError` will be thrown.

A concrete subtype of `AbstractGeometry` must implement

```
transform(ent::MyEntity, f::Transformation)
```

It is not, however, required that an arbitrary `Transformation` be valid on `MyEntity`. For example, one might write

```julia
transform(ent::MyEntity, f::Transformation) = transform(ent, ScaledIsometry(f))
function transform(ent::MyEntity, f::ScaledIsometry)
    # ... create and return transformed entity
end
```

which will throw a `DomainError` if `!preserves_angles(f)` (`f` is not a scaled isometry).
