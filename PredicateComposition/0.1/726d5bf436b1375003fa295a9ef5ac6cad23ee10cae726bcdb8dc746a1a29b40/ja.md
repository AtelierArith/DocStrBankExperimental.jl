```julia
ISEQUAL(f1,f2) = (args...) -> f1(args...) == f2(args...)
ISEQUAL(f1,n::Number) = (args...) -> f1(args...) == n
```
