```
JLFunction(ex::Expr)
```

Julia関数`Expr`から`JLFunction`オブジェクトを作成します。

# 例

```julia
julia> JLFunction(:(f(x) = 2))
f(x) = begin
    #= REPL[37]:1 =#    
    2    
end
```
