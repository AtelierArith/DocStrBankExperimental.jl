```
codegen_ast_struct_body(def)
```

Generate the struct body.

# Example

```julia
julia> def = JLStruct(:(struct Foo
           x::Int
           
           Foo(x::Int) = new(x)
       end))
struct Foo
    x::Int
end

julia> codegen_ast_struct_body(def)
quote
    #= REPL[15]:2 =#
    x::Int
    Foo(x::Int) = begin
            #= REPL[15]:4 =#
            new(x)
        end
end
```
