```
JLStruct(ex::Expr)
```

Juliaの構造体`Expr`から`JLStruct`オブジェクトを作成します。

# 例

```julia
julia> JLStruct(:(struct Foo
           x::Int
       end))
struct Foo
    #= REPL[38]:2 =#
    x::Int
end
```
