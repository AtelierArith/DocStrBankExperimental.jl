```
popov_with_transform(A::MatElem{T}) where {T <: PolyRingElem}
```

タプル $(P, U)$ を計算します。ここで $P$ は $A$ のポポフ形式であり、$U$ は $P = UA$ となる変換行列です。
