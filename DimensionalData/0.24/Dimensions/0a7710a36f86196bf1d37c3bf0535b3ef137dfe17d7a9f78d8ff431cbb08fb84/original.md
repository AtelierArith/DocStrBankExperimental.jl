m     Ti <: TimeDim

```
Ti(val=:)
```

Time [`Dimension`](@ref). `Ti <: TimeDim <: IndependentDim`

`Time` is already used by Dates, and `T` is a common type parameter, We use `Ti` to avoid clashes.

## Example:

```julia
timedim = Ti(DateTime(2021, 1):Month(1):DateTime(2021, 12))
# Or
val = A[Ti(1)]
# Or
mean(A; dims=Ti)
```
