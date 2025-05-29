```
operate!(op::Function, args...)
```

`args[1]`の値を`op(args...)`の値と等しくなるように変更します。`mutability(args[1], op, args...)`が[`IsMutable`](@ref)を返す場合にのみ呼び出すことができます。
