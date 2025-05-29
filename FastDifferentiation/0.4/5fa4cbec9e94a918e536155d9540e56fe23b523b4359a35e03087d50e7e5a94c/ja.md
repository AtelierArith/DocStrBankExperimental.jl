```
sparse_jacobian(
    terms::AbstractVector{<:Node},
    partial_variables::AbstractVector{<:Node}
)
```

`terms`で定義された関数のヤコビ行列を含む疎配列を返します。
