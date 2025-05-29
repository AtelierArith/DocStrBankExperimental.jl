```
log(M::SymmetricPositiveSemidefiniteFixedRank, q, p)
```

[`SymmetricPositiveSemidefiniteFixedRank`](@ref) 多様体上で、$Y$に関して $\lVert p - qY\rVert$ を最小化することによって対数写像を計算します。

!!! note
    多様体は埋め込みで表現されており、商多様体であるため、指数写像と対数写像は同値類に関してのみ全単射です。計算すると

    $$
        q_2 = \exp_p(\log_pq)
    $$

    行列 $q_2≠q$ が得られるかもしれませんが、これは商多様体上で同じ点を表しています。すなわち、$d_{\operatorname{SPS}_k(n)}(q_2,q) = 0$ です。

