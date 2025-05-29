```
isTypeDataType(@nospecialize t) -> Bool
```

型 `t` に対して、∀S s.t. `isa(S, rewrap_unionall(Type{t}, ...))` の場合、`isa(S, DataType)` であるかをテストします。特に、あるステートメントが `Type{t}` として型付けされている場合（潜在的にいくつかの `UnionAll` にラップされている可能性があります）、このステートメントがランタイムで `DataType` であることが保証されます（例えば、`Union` や `UnionAll` 型と等しいものではありません）。
