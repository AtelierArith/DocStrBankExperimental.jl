```
moving(f, ta::TimeArray{T,1}, w::Integer; padding = false)
```

Apply user-defined function `f` to a 1D `TimeArray` with window size `w`.

## Example

To calculate the simple moving average of a time series:

```julia
moving(mean, ta, 10)
```
