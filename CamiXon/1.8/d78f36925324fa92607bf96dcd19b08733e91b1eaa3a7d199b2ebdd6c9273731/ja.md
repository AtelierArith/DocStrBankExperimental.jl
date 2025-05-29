```
rotbarrier(grid::CamiDiff.Grid{T}; ℓ=0) where T<:Real
```

CamiDiff.Grid の回転バリアポテンシャルの表現（波数表記）、

$$
V_{rot}(r) = \frac{\ell(\ell+1)}{r^{2}},
$$

ここで ℓ は回転量子数です。
