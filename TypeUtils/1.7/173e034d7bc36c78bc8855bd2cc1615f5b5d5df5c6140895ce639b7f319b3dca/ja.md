```
to_same_concrete_type(Ts::Type...) -> T::Type
```

は `T = promote_type(Ts...)` を返し、`T` が具体的な型でない場合は例外をスローします。

また、[`to_same_type`](@ref)も参照してください。
