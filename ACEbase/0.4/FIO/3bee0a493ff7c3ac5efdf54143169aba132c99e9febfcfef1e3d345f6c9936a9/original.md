`read_dict(D::Dict) -> ?`

Looks for a key `__id__` in `D` whose value is used to dynamically dispatch the decoding to

```julia
read_dict(Val(Symbol(D["__id__"])), D)
```

That is, a user defined type must implement this `convert(::Val, ::Dict)` utility function. The typical code would be

```julia
module MyModule
    struct MyStructA
        a::Float64
    end
    Dict(A::MyStructA) = Dict( "__id__" -> "MyModule_MyStructA",
                               "a" -> a )
    MyStructA(D::Dict) = A(D["a"])
    Base.convert(::Val{:MyModule_MyStructA})
end
```

The user is responsible for choosing an id that is sufficiently unique.

The purpose of this function is to enable the loading of more complex JSON files and automatically converting the parsed Dict into the appropriate composite types. It is intentional that a significant burden is put on the user code here. This will maximise flexibiliy, e.g., by introducing version numbers, and being able to read old version in the future.
