```
batched_vec(A::Array{T,3}, B::Matrix)
batched_vec(A::Array{T,3}, b::Vector)
```

バッチ行列-ベクトル乗算：結果は `C[:,:,k] == A[:,:,k] * B[:,k]` であり、すべての `k` に対して成り立つか、または `C[:,:,k] == A[:,:,k] * b` である（`b::Vector` の場合）。

同じ引数の型で、`batched_mul(A, B)` は `B` を固定行列として扱い、ベクトルのバッチとは見なさない。両方をリシェイプしてから `batched_mul(::Array{T,3}, ::Array{T,3})` を呼び出す。

```jldoctest
julia> A, B, b = randn(16,8,32), randn(8,32), randn(8);

julia> batched_vec(A,B) |> size
(16, 32)

julia> batched_vec(A,b) |> size
(16, 32)
```
