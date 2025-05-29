```
h5open(f::Function, args...; pv...)
```

Apply the function f to the result of `h5open(args...; kwargs...)` and close the resulting `HDF5.File` upon completion. For example with a `do` block:

```
h5open("foo.h5","w") do h5
    h5["foo"]=[1,2,3]
end
```
