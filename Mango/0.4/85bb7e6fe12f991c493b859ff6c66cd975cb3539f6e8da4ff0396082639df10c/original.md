This macro can be applied to struct definitions and adds the possibility to define default values on field declaration. In contrast to @kwdef or @with_kw, this macro will create normal parameters for construction if no default value has been provided.

# Example

```julia
@with_def struct ExampleStruct
    abc::Int = 0
    def::String
end

# can be constructed as follows
es = ExampleStruct("mydefstring") # abc == 0
es = ExampleStruct("mydefstring", abc=3) # abc == 3
```
