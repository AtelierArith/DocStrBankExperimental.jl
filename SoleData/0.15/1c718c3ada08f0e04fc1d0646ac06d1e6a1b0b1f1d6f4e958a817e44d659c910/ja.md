```
struct MultivariateFeature{U} <: VarFeature
    f::Function
end
```

次元チャネルに関数を適用することによって表される次元特徴。例えば、画像上で解釈されたときに `Interval2D` の世界がどれだけ馬に似ているかを計算するスカラー関数をラップすることができます。画像には空間変数がいくつかあります（RGBの場合は3つ）、「馬に似ている」ということはすべての変数を含む計算を必要とするかもしれません。

関連情報としては、[`SoleLogics.Interval`](@ref)、[`SoleLogics.Interval2D`](@ref)、[`AbstractUnivariateFeature`](@ref)、[`VarFeature`](@ref)、[`AbstractFeature`](@ref)があります。
