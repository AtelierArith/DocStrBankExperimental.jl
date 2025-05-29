```julia
ISGREATEREQ(f1,f2) = (args...) -> f1(args...) >= f2(args...)
ISGREATEREQ(f1,n::Number) = (args...) -> f1(args...) >= n
```
