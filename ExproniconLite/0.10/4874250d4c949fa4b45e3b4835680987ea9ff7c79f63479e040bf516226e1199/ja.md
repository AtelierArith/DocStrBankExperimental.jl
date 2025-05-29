```
JLKwStruct(ex::Expr, typealias=nothing)
```

与えられたJulia構造体`Expr`から`JLKwStruct`を作成し、この型名にエイリアスを付けるオプションがあります。

# 例

```julia
julia> JLKwStruct(:(struct Foo
           x::Int = 1
       end))
#= kw =# struct Foo
    #= REPL[39]:2 =#
    x::Int = 1
end
```
