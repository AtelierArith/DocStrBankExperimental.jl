```
otheridxs(A::ClimArray, Dim)
```

Return an iterator of indices, that when used can access all indices of `A` *except* those belonging to dimension(s) `Dim`.

For example, if `A` has dims `(Lon, Lat, Time)` you can get all timeseries of `A`:

```julia
for i in otheridxs(A, Time())
    x = A[i...] # this is a timeseries (Vector) for each lon × lat combination
end
```

or all time+latitude slices with

```julia
for i in otheridxs(A, (Time(), Lat()))
    x = A[i...] # matrix of time × latitude slice for each longitude
end
```

(notice that splatting `i...` is necessary because `otheridxs` generates tuples)
