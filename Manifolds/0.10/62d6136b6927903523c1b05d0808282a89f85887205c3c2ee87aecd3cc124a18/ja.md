```
log(M::AbstractSphere, p, q)
```

[`AbstractSphere`](@ref) `M`上の対数写像を計算します。すなわち、点`p`から出発する測地線が時間1で点`q`に到達する接ベクトルです。式は次のようになります（$x ≠ -y$の場合）：

$$
\log_p q = d_{𝕊}(p,q) \frac{q-\Re(⟨p,q⟩) p}{\lVert q-\Re(⟨p,q⟩) p \rVert_2},
$$

そして、$x=-y$の場合、すなわち対向点に対しては接ベクトルの集合から決定論的な選択が返されます。
