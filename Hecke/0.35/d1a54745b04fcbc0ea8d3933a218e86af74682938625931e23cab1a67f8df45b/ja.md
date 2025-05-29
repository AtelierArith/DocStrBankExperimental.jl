```
is_locally_represented_by(U::T, V::T, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) where T <: AbstractSpace -> Bool
```

同じ代数 `E` 上の二つの空間 `U` と `V` と、彼らの固定体 `K` の最大順序 $\mathcal O_K$ における素イデアル `p` が与えられたとき、`U` が `p` において `V` に局所的に表されるかどうか、すなわち $U_p$ が $V_p$ に埋め込まれるかどうかを返します。
