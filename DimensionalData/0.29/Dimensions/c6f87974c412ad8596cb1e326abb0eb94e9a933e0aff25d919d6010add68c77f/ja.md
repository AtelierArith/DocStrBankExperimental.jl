m     Ti <: TimeDim

```
Ti(val=:)
```

Time [`Dimension`](@ref). `Ti <: TimeDim <: IndependentDim`

`Time`はすでにDatesによって使用されており、`T`は一般的な型パラメータです。衝突を避けるために`Ti`を使用します。

## 例:

```julia
timedim = Ti(DateTime(2021, 1):Month(1):DateTime(2021, 12))
```

```julia
val = A[Ti(1)]
```

```julia
mean(A; dims=Ti)
```
