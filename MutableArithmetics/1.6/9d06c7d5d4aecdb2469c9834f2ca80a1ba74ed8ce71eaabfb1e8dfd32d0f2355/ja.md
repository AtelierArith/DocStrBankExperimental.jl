```
buffered_operate_to!(buffer, output, op::Function, args...)
```

`output`の値を`op(args...)`の値と等しくなるように変更します。これにより、`buffer`が変更される可能性があります。`mutability(output, op, args...)`が[`IsMutable`](@ref)を返す場合にのみ呼び出すことができます。
