```
measurement(::ContinuousHistogram)
```

[`Measurements.jl`](https://juliaphysics.github.io/Measurements.jl/stable/)へのインターフェース。`val`を[`ContinuousHistogram`](@ref)の[`mean`](@ref)として、`err`を[`ContinuousHistogram`](@ref)の[`std`](@ref)（標準偏差）として持つ`Measurement`を返します。

!!! warning
    問題の[`ContinuousHistogram`](@ref)が著しく非ガウス的である場合、最初の2つの統計的[累積量](https://en.wikipedia.org/wiki/Cumulant?oldformat=true)では、基礎となる分布を適切に記述するには不十分な場合があります。この意味で、`measurement = value ± error`はデータを記述するのに意味がないかもしれません。

