```
ParaxialInterface{T} <: OpticalInterface{T}
```

理想化された平面レンズを記述するインターフェース、すなわち薄く、収差のないレンズです。

**一般的に、このインターフェースは直接構築すべきではなく、`ParaxialLensEllipse`および`ParaxialLensRect`関数を使用して直接[`ParaxialLens`](@ref)オブジェクトを作成するべきです。**

```julia
ParaxialInterface(focallength::T, centroid::SVector{3,T}, outsidematerial::Y)
```
