```
TensorField{B,F,N} <: GlobalFiber{LocalTensor{B,F},N}
```

Defines a `GlobalFiber` type with `eltype` of `LocalTensor{B,F}` and `immersion`.

```Julia
coordinates(s) # ::AbstractArray{B,N}
fiber(s) # ::AbstractArray{F,N}
points(s) # ::AbstractArray{P,N}
metricextensor(s) # ::AbstractArray{G,N}
coordinatetype(s) # B
fibertype(s) # F
pointtype(s) # P
metrictype(s) # G
immersion(s) # ::ImmersedTopology
```

Various methods work on any `TensorField`, such as `base`, `fiber`, `coordinates`, `points`, `metricextensor`, `basetype`, `fibertype`, `coordinatetype`, `pointtype`, `metrictype`, `immersion`. Due to the versatility of the `TensorField` type instances, it's possible to disambiguate them into these type alias specifications with associated methods: `ElementMap`, `SimplexMap`, `FaceMap`, `IntervalMap`, `RectangleMap`, `HyperrectangleMap`, `ParametricMap`, `Variation`, `RealFunction`, `PlaneCurve`, `SpaceCurve`, `AbstractCurve`, `SurfaceGrid`, `VolumeGrid`, `ScalarGrid`, `DiagonalField`, `EndomorphismField`, `OutermorphismField`, `CliffordField`, `QuaternionField`, `ComplexMap`, `PhasorField`, `SpinorField`, `GradedField{G} where G`, `ScalarField`, `VectorField`, `BivectorField`, `TrivectorField`.

In the `Cartan` package, a technique is employed where a `TensorField` is constructed from an interval, product manifold, or topology, to generate an algebra of sections which can be used to compose parametric maps on manifolds. Constructing a `TensorField` can be accomplished in various ways, there are explicit techniques to construct a `TensorField` as well as implicit methods. Additional packages such as `Adapode` build on the `TensorField` concept by generating them from differential equations. Many of these methods can automatically generalize to higher dimensional manifolds and are compatible with discrete differential geometry.
