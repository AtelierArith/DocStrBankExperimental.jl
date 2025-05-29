```
codegen_ast_struct(def)
```

Generate pure Julia struct `Expr` from struct definition. This is equivalent to `codegen_ast` for `JLStruct`. See also [`codegen_ast`](@ref).

# Example

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
