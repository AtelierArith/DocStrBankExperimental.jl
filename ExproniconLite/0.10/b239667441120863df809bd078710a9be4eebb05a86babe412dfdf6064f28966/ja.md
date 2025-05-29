```
codegen_ast_kwfn(def[, name = nothing])
```

Juliaの構造体定義からキーワード関数を生成します。

# 例

```julia
julia> def = @expr JLKwStruct struct Foo{N, T}
                  x::T = 1
              end
#= kw =# struct Foo{N, T}
    #= REPL[19]:2 =#
    x::T = 1
end

julia> codegen_ast_kwfn(def)|>prettify
quote
    function Foo{N, T}(; x = 1) where {N, T}
        Foo{N, T}(x)
    end
    function Foo{N}(; x::T = 1) where {N, T}
        Foo{N, T}(x)
    end
end

julia> def = @expr JLKwStruct struct Foo
                  x::Int = 1
              end
#= kw =# struct Foo
    #= REPL[23]:2 =#
    x::Int = 1
end

julia> codegen_ast_kwfn(def)|>prettify
quote
    function Foo(; x = 1)
        Foo(x)
    end
    nothing
end
```
