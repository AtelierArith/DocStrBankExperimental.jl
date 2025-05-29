```
-(a::IntExpr)
-(r::RealExpr)
```

Return the negative of an Int or Real expression.

```julia
@satvariable(a[1:n, 1:m], Int)
-a # this also works
```
