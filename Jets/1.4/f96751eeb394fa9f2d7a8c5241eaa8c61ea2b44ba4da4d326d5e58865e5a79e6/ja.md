```
shape(A[, i])
```

`A::Union{Jet, Jop, AbstractMatrix}`の範囲と定義の形状を返します。引数がない場合、`(size(range(A)), size(domain(A)))`を返します。`i`が指定されている場合、`i = 1`のときは`size(range(A))`を返し、それ以外の場合は`size(domain(A))`を返します。
