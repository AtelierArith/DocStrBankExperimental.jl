```
is_enum(EnumPattern)::Bool
```

パターン `EnumPattern` を `EnumPattern()` に変換します。

例:     ```     abstract type AbsS end     struct S1 <: AbsS end     struct S2 <: AbsS end     MLStyle.pattern*uncall(::Type{S}, self, _, _, _) where {S<:AbsS} = literal(S())     MLStyle.is*enum(::Type{<:AbsS}) = true

``x = S1() @match x begin     S2 => 1     S1 => 2 end`
