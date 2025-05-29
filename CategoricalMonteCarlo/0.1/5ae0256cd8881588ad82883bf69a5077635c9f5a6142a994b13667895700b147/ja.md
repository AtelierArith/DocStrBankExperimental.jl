```
sample!(B::AbstractArray, A::AbstractArray)
```

サンプルを引き出し、`B` にインプレースで合計（および潜在的に削減）します。`B` の形状が実行される削減の範囲を決定します。

関連情報: [`tsample!`](@ref), [`vsample!`](@ref), [`vtsample!`](@ref)
