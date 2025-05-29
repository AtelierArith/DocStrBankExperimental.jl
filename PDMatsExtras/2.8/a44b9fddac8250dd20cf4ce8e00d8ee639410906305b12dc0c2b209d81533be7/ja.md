```
WoodburyPDMat(
    A::AbstractMatrix{T}, D::Diagonal{T}, S::Diagonal{T},
) where {T<:Real}
```

遅延評価で次の形の行列を表します

```julia
W = A * D * A' + S
```

`D` と `S` は非負のエントリのみを持つ必要があります。

この行列型を使用するのは、`size(A, 1) > size(A, 2)` の場合に良いアイデアです。行列内の構造を利用して、`W` の逆行列 [1] に関わる操作や、行列式 [2] に関わる操作（例えば `invquad` や `logdet`）を加速できます。

`size(A, 1) < size(A, 2)` の場合は、この行列型を使用しない方が良いでしょう。

[1] - https://en.wikipedia.org/wiki/Woodbury*matrix*identity [2] - https://en.wikipedia.org/wiki/Matrix*determinant*lemma
