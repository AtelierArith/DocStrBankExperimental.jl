```julia
ISLESS(f1,f2) = (args...) -> f1(args...) < f2(args...)
ISLESS(f1,n::Number) = (args...) -> f1(args...) < n
```
