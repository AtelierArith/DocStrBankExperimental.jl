```
extended_weak_popov(A::MatElem{T}, V::MatElem{T}) where {T <: PolyRingElem}
```

行列 $A$ に対して単純な行変換を適用し、ベクトル $V$ に対して同じ変換を適用することによって、$A$ の弱ポポフ形式 $P$ を計算します。タプル $(P, W)$ を返します。
