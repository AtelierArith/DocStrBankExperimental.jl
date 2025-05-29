```julia
SUM(fs...) = (args...) -> +((f(args...) for f in fs)...)
```
