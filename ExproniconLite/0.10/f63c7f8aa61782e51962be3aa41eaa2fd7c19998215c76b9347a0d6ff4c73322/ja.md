```
@expr <type> <expression>
```

指定された型の式を返します。

# 例

```julia
julia> ex = @expr JLKwStruct struct Foo{N, T}
           x::T = 1
       end
#= kw =# struct Foo{N, T}
    #= /home/roger/code/julia/Expronicon/test/analysis.jl:5 =#
    x::T = 1
end
```
