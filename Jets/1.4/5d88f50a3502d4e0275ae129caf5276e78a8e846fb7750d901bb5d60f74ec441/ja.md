```
state(A::Union{Jet,Jop,JopAdjoint}[, key])
```

`key::Symbol` が指定されている場合、`key` に対応する状態を返します。そうでない場合は、Aの状態を `NamedTuple` として返します。
