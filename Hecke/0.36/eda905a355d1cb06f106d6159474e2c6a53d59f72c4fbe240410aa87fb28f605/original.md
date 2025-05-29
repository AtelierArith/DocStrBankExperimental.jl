```
crt_env(p::Vector{T}) -> crt_env{T}
```

Given coprime moduli in some euclidean ring (ZZ, zzModRingElem_poly, ZZRingElem_mod_poly), prepare data for fast application of the chinese remainder theorem for those moduli.
