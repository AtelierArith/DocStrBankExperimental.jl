```
macro add_init(symbol::Symbol)

Automatically add a construction method for building objects with dict and json 
to the DataType, and adapt to the DataType modified by base.@kwdef
```

# Examples:

```julia
    @Base.kwdef struct Test
        a::Int
        b::Int=2
        c::Int
    end
    @add_init Test

    Test(Dict("a"=>1, "c"=>3)) == Test(1,2,3)
```
