```
hnf_modular(M::MatElem{T}, d::T, is_prime::Bool = false)
```

`is_prime`が設定されている場合、`vcat(M, identity_matrix(parent(d), ncols(M)))`の`hnf`を返します。その場合、内部的には`hnf`の代わりに、剰余体モジュロ`d`上の`rref`が使用されます。
