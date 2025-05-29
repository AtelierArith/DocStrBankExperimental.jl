m     Ti <: TimeDim

```
Ti(val=:)
```

時間 [`Dimension`](@ref). `Ti <: TimeDim <: IndependentDim`

`Time` はすでに Dates によって使用されており、`T` は一般的な型パラメータです。衝突を避けるために `Ti` を使用します。

## 例:

```julia
timedim = Ti(DateTime(2021, 1):Month(1):DateTime(2021, 12))
# または
val = A[Ti(1)]
# または
mean(A; dims=Ti)
```
