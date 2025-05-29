```
buffered_operate!(buffer, op::Function, args...)
```

`args[1]`の値を`op(args...)`の値と等しくなるように変更します。これにより、`buffer`が変更される可能性があります。`mutability(args[1], op, args...)`が[`IsMutable`](@ref)を返す場合にのみ呼び出すことができます。
