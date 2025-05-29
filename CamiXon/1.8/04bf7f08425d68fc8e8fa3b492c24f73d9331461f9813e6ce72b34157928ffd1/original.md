```
primitivetype(T::Type)
```

The primitive type of a Type

#### Examples:

```
julia> T = Complex{Float16}};
julia> primitivetype(T)
Float16

julia> T = String
julia> primitivetype(T)
Char
```
