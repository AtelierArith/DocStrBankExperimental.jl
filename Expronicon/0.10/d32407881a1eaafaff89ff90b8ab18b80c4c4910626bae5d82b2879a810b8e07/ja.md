```
codegen_ast(def)
```

与えられた構文タイプからJulia ASTオブジェクト`Expr`を生成します。

# 例

`JLKwStruct`構文タイプからJulia ASTオブジェクトを生成できます。

```julia
julia> def = @expr JLKwStruct struct Foo{N, T}
                  x::T = 1
              end
#= kw =# struct Foo{N, T}
    #= REPL[19]:2 =#
    x::T = 1
end

julia> codegen_ast(def)|>rm_lineinfo
quote
    struct Foo{N, T}
        x::T
    end
    begin
        function Foo{N, T}(; x = 1) where {N, T}
            Foo{N, T}(x)
        end
        function Foo{N}(; x::T = 1) where {N, T}
            Foo{N, T}(x)
        end
    end
end
```
