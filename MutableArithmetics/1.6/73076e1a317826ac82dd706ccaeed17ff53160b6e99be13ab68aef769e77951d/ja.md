```
mutability(T::Type, ::typeof(op), args::Type...)::MutableTrait
```

型 `T` のオブジェクトが `op(args...)` と等しくなるように変更できることを示すには [`IsMutable`](@ref) を返し、そうでない場合は [`IsNotMutable`](@ref) を返します。
