```
atol(T)
atol(x::T)
```

型 `T` の数値との近似比較に使用される絶対許容誤差。これは、[`isapprox`](@ref) 関数への呼び出しのソースコードで使用されます：

```julia
isapprox(a::T, b::T, atol=atol(T))
```
