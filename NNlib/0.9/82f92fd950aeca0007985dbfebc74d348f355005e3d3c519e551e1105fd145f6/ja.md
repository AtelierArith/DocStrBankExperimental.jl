```
batched_mul(A, B) -> C
A ⊠ B  # \boxtimes
```

バッチ行列乗算。結果は `C[:,:,k...] == A[:,:,k...] * B[:,:,k...]` であり、ここで `k...` は最後の次元の任意のインデックスを表します。

もし `ndims(A) == ndims(B) == 3` かつ `size(B,3) == 1` の場合、代わりに `C[:,:,k] == A[:,:,k] * B[:,:,1]` となり、`A` に対しても同様です。

各行列を転置するには、配列に `batched_transpose` を適用するか、共役転置には `batched_adjoint` を使用します：

```jldoctest
julia> A, B = randn(2,5,17), randn(5,9,17);

julia> A ⊠ B |> size
(2, 9, 17)

julia> batched_adjoint(A) |> size
(5, 2, 17)

julia> batched_mul(A, batched_adjoint(randn(9,5,17))) |> size
(2, 9, 17)

julia> A ⊠ randn(5,9,1) |> size
(2, 9, 17)

julia> batched_transpose(A) == PermutedDimsArray(A, (2,1,3))
true
```

同等の `PermutedDimsArray` は `batched_transpose` の代わりに使用できます。他の置換も BLAS によって処理されますが、バッチインデックス `k` が基になる配列の最初の次元でない限りです。したがって、`PermutedDimsArray(::Array, (1,3,2))` および `PermutedDimsArray(::Array, (3,1,2))` は問題ありません。

しかし、`A = PermutedDimsArray(::Array, (3,2,1))` は BLAS にとって受け入れられません。なぜなら、バッチ次元が連続しているからです：`stride(A,3) == 1`。これにより、`batched_mul_generic!` よりも速いため、コピーされます。

この `copy` と `batched_mul_generic!` の両方は `@debug` メッセージを生成し、例えば `ENV["JULIA_DEBUG"] = NNlib` を設定すると、それらが表示されます。
