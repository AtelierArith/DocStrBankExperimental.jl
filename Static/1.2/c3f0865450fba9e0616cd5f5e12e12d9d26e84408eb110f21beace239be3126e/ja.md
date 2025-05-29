```
known(T::Type)
```

静的型 `T` に対応する既知の値を返します。`T` が静的型でない場合は `nothing` が返されます。

`known` は、コンパイラが正確な値を推論できなくても、返される値の型が常に推論されることを保証します。

参照: [`static`](@ref), [`is_static`](@ref), [`dynamic`](@ref)

# 例

```julia
julia> known(StaticInt{1})
1

julia> known(Int)

```
