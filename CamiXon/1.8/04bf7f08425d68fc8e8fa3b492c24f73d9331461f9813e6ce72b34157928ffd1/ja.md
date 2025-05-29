```
primitivetype(T::Type)
```

Typeの原始型

#### 例:

```
julia> T = Complex{Float16}};
julia> primitivetype(T)
Float16

julia> T = String
julia> primitivetype(T)
Char
```
