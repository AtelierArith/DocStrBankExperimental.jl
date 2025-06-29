```
mb03vd!(n::Integer, p::Integer, ilo::Integer, ihi::Integer, A::Array{Float64, 3}, tau::AbstractMatrix{Float64}) -> info::Int64
```

`A = A_1*A_2*...*A_p` の `p` 個の実一般行列の積を上ヘッセンベルグ形式 `H = H_1*H_2*...*H_p` に変換します。ここで、`H_1` は上ヘッセンベルグ行列であり、`H_2`, ..., `H_p` は上三角行列です。これは、`A` に対して直交類似変換を使用して行います。

```
    Q_1' * A_1 * Q_2 = H_1,
    Q_2' * A_2 * Q_3 = H_2,
           ...
    Q_p' * A_p * Q_1 = H_p.
```

行列 `A_1`, `A_2`, ..., `A_p` は3次元配列 `A` に含まれています。結果として得られる `H_1`, `H_2`, ..., `H_p` および `Q_1`, `Q_2`, ..., `Q_p` は、`A` 内の `A_1`, `A_2`, ..., `A_p` と配列 `tau` を上書きします。

詳細については、`MB03VD` の SLICOT ドキュメントを参照してください。
