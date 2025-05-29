```
read_only(daf::DafReader[; name::Maybe{AbstractString]} = nothing)::DafReadOnlyWrapper
```

`daf`を[`DafReadOnlyWrapper`](@ref)でラップして、偶発的な変更から保護します。指定されていない場合、`daf`の`name`が再利用されます。`name`が指定されておらず、`daf`が[`DafReadOnly`](@ref)である場合は、そのまま返します。
