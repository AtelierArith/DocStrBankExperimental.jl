```
apply(f, target::Union{TraitTarget, GI.AbstractTrait}, obj; kw...)
```

Reconstruct a geometry, feature, feature collection, or nested vectors of either using the function `f` on the `target` trait.

`f(target_geom) => x` where `x` also has the `target` trait, or a trait that can be substituted. For example, swapping `PolgonTrait` to `MultiPointTrait` will fail if the outer object has `MultiPolygonTrait`, but should work if it has `FeatureTrait`.

Objects "shallower" than the target trait are always completely rebuilt, like a `Vector` of `FeatureCollectionTrait` of `FeatureTrait` when the target has `PolygonTrait` and is held in the features. These will always be GeoInterface  geometries/feature/feature collections. But "deeper" objects may remain unchanged or be whatever GeoInterface compatible objects `f` returns.

The result is a functionally similar geometry with values depending on `f`.

  * `threaded`: `true` or `false`. Whether to use multithreading. Defaults to `false`.
  * `crs`: The CRS to attach to geometries. Defaults to `nothing`.
  * `calc_extent`: `true` or `false`. Whether to calculate the extent. Defaults to `false`.

## Example

Flipped point the order in any feature or geometry, or iterables of either:

```julia
import GeoInterface as GI
import GeometryOps as GO
geom = GI.Polygon([GI.LinearRing([(1, 2), (3, 4), (5, 6), (1, 2)]),
                   GI.LinearRing([(3, 4), (5, 6), (6, 7), (3, 4)])])

flipped_geom = GO.apply(GI.PointTrait, geom) do p
    (GI.y(p), GI.x(p))
end
```
