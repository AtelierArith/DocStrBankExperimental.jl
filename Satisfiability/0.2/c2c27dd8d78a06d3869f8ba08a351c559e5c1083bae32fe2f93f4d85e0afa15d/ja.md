```
-(a::IntExpr)
-(r::RealExpr)
```

整数または実数の式の負を返します。

```julia
@satvariable(a[1:n, 1:m], Int)
-a # これも動作します
```
