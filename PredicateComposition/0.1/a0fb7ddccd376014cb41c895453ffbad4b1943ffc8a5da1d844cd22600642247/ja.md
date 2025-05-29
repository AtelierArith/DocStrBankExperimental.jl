```julia
MIN(fs...) = (args...) -> min((f(args...) for f in fs)...)
```
