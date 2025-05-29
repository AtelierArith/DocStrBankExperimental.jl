```
exp(M::SymmetricPositiveSemidefiniteFixedRank, q, Y)
```

[`SymmetricPositiveSemidefiniteFixedRank`](@ref)上の指数写像を計算します。これは次のように表されます。

$$
    \exp_q Y = q+Y.
$$

!!! note
    マンフォールドは埋め込みで表現され、商マンフォールドであるため、指数写像と対数写像は同値類に関してのみ全単射です。

    $$
        q_2 = \exp_p(\log_pq)
    $$

    を計算すると、行列 $q_2\neq q$ が得られるかもしれませんが、これは商マンフォールド上の同じ点を表します。すなわち、$d_{\operatorname{SPS}_k(n)}(q_2,q) = 0$ です。

