```
central_fdm(f::Function, x::Float64; ϵ=0.01)
```

Simple central differences implementation. 

FiniteDifferences.jl does not work with AD so I implemented this manually. Still remains to test this with FiniteDiff.jl
