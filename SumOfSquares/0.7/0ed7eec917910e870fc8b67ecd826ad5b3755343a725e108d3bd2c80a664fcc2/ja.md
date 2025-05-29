```
struct GramMatrix{T, B, U, MT <: AbstractMatrix{T}} <: AbstractGramMatrix{T, B, U}
    Q::MT
    basis::B
end
```

グラム行列 $x^\top Q x$ で、`Q` は基底 `basis` の多項式ベクトルによってインデックス付けされた対称行列です。
