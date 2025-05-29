```
macro add_init(type::Expr)

Automatically add a constructor for building objects with dict and json to DataType
```

# Examples:

```julia
    @add_init struct Test
        field:AbstractString
    end

    Test("{"field":"a"}") == Test("a")
    Test(Dict("field"=>"a")) == Test("a")
```
