```
moving(f, ta::TimeArray{T,2}, w::Integer; padding = false, dims = 1, colnames = [...])
```

## Example

In case of `dims = 2`, the user-defined function `f` will get a 2D `Array` as input.

```julia
moving(ohlc, 10, dims = 2, colnames = [:A, ...]) do
    # given that `ohlc` is a 500x4 `TimeArray`,
    # size(A) is (10, 4)
    ...
end
```
