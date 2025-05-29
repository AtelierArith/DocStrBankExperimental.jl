```
is_enum(EnumPattern)::Bool
```

Convert the pattern `EnumPattern` to `EnumPattern()`.

e.g.,     ```     abstract type AbsS end     struct S1 <: AbsS end     struct S2 <: AbsS end     MLStyle.pattern*uncall(::Type{S}, self, _, _, _) where {S<:AbsS} = literal(S())     MLStyle.is*enum(::Type{<:AbsS}) = true

````
x = S1()
@match x begin
    S2 => 1
    S1 => 2
end
```
````
