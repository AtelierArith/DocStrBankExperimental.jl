Uses linear interpolation to fill for missing values. This function work for any kind of array, and not just nighttime lights radiance time series data. 

```
x = rand(1:10.0, 10)
x = Vector{Union{Missing, Float64}}(x)
x[5] = missing
na_interp_linear(x)
```
