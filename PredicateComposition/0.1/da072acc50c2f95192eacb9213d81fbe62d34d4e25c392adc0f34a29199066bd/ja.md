```julia
MAX(fs...) = (args...) -> max((f(args...) for f in fs)...)
```
