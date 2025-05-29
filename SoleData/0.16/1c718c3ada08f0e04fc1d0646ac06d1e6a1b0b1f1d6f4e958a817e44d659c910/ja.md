```
struct MultivariateFeature{U} <: VarFeature
    f::Function
end
```

関数の適用によって表される多次元特徴。例えば、画像上で解釈されたときに `Interval2D` の世界がどれだけ馬に似ているかを計算するスカラー関数をラップすることができます。画像にはいくつかの空間変数（RGBの場合は3つ）があり、「馬に似ている」ということはすべての変数を含む計算を必要とするかもしれません。

関連情報としては、[`SoleLogics.Interval`](@ref)、[`SoleLogics.Interval2D`](@ref)、[`AbstractUnivariateFeature`](@ref)、[`VarFeature`](@ref)、[`AbstractFeature`](@ref)があります。
