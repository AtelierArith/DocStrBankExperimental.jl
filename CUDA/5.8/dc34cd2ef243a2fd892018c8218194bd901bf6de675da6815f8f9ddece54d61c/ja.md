```
attribute(X, ptr::Union{Ptr,CuPtr}, attr)
```

ポインタ `ptr` に関する属性 `attr` を返します。返される値の型は属性によって異なるため、`X` パラメータとして渡す必要があります。
