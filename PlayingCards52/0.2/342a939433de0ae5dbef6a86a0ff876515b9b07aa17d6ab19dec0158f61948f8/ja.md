```
name(C::Card)::String
```

カードの長い名前を返します。

```julia
julia> c = Card(:diamonds, 10)
T♢

julia> name(c)
"ten of diamonds"
```
