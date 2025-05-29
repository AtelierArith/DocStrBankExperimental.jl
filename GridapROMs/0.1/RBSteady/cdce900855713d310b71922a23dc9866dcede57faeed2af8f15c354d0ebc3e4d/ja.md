```
abstract type Projection <: Map end
```

`N`次元ベクトル空間の`n`次元ベクトル部分空間の基底を表し（`N >> n`）、Galerkin射影演算子として使用されます。Projectionのカーネルは`n`次元ですが、その像は`N`次元です。

サブタイプ:

  * [`PODProjection`](@ref)
  * [`TTSVDProjection`](@ref)
  * [`NormedProjection`](@ref)
  * [`BlockProjection`](@ref)
  * [`InvProjection`](@ref)
  * [`ReducedProjection`](@ref)
  * [`HyperReduction`](@ref)
