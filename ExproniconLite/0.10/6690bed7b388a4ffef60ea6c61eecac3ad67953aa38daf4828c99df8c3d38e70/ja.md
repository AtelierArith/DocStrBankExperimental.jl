```
codegen_ast_struct(def)
```

純粋なJulia構造体`Expr`を構造体定義から生成します。これは`JLStruct`に対する`codegen_ast`と同等です。詳細は[`codegen_ast`](@ref)を参照してください。

# 例

```julia-repl
julia> def = JLKwStruct(:(struct Foo
           x::Int=1
           
           Foo(x::Int) = new(x)
       end))
struct Foo
    x::Int = 1
end

julia> codegen_ast_struct(def)
:(struct Foo
      #= REPL[21]:2 =#
      x::Int
      Foo(x::Int) = begin
              #= REPL[21]:4 =#
              new(x)
          end
  end)
```
