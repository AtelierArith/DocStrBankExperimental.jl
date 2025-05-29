```
extended_weak_popov_with_transform(A::MatElem{T}, V::MatElem{T}) where {T <: PolyRingElem}
```

行列 $A$ に対して単純な行変換を適用することによって $A$ の弱ポポフ形式 $P$ を計算し、同じ変換をベクトル $V$ に適用してベクトル $W$ を得て、$P = UA$ となる変換行列 $U$ を得ます。タプル $(P, W, U)$ を返します。
