Only for use when RME functions return non-error numeric results.

# Examples

```julia
count_per_m2::Float64 = @getRME ivOutplantCountPerM2("iv_name"::Cstring)::Cdouble
```
