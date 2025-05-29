```
TensorField{B,F,N} <: GlobalFiber{LocalTensor{B,F},N}
```

`LocalTensor{B,F}`の`eltype`と`immersion`を持つ`GlobalFiber`型を定義します。

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

`TensorField`に対しては、`base`、`fiber`、`coordinates`、`points`、`metricextensor`、`basetype`、`fibertype`、`coordinatetype`、`pointtype`、`metrictype`、`immersion`などのさまざまなメソッドが機能します。`TensorField`型のインスタンスの多様性により、これらの型エイリアス仕様に関連するメソッドに分解することが可能です：`ElementMap`、`SimplexMap`、`FaceMap`、`IntervalMap`、`RectangleMap`、`HyperrectangleMap`、`ParametricMap`、`Variation`、`RealFunction`、`PlaneCurve`、`SpaceCurve`、`AbstractCurve`、`SurfaceGrid`、`VolumeGrid`、`ScalarGrid`、`DiagonalField`、`EndomorphismField`、`OutermorphismField`、`CliffordField`、`QuaternionField`、`ComplexMap`、`PhasorField`、`SpinorField`、`GradedField{G} where G`、`ScalarField`、`VectorField`、`BivectorField`、`TrivectorField`。

`Cartan`パッケージでは、`TensorField`が区間、積多様体、またはトポロジーから構築され、マニホールド上のパラメトリックマップを構成するために使用できるセクションの代数を生成する技術が採用されています。`TensorField`を構築する方法はいくつかあり、明示的な技術と暗黙的な方法があります。`Adapode`などの追加パッケージは、微分方程式から`TensorField`を生成することによってこの概念を拡張します。これらの多くの方法は、自動的に高次元の多様体に一般化でき、離散微分幾何学と互換性があります。
