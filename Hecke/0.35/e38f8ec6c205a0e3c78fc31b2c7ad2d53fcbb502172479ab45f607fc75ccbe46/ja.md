```
mul_sparse(A::SMat{T}, B::SMat{T}) -> SMat{T}
```

スパース行列として $A\cdot B$ の積を返します。

一般に、2つのスパース行列の積はスパースではないため、文脈によっては [`mul_dense(::SMat{T}, ::SMat{T}) where {T}`](@ref) を使用する方が効率的かもしれません。
