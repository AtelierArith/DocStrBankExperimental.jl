```
CalcDoubleIntegral(f::Function, a::Real, b::Real, c::Real, d::Real, n::UInt64)
```

Compute double integral of f(x,y) function over domain D=[a, b] x [c(a), d(b)](Double Simpson's method).

```
b                        
.- d(x)                  
|    .-                  
|    |                   
|   -'  f(x, y) . dy . dx
-'  c(x)                  
a
```
