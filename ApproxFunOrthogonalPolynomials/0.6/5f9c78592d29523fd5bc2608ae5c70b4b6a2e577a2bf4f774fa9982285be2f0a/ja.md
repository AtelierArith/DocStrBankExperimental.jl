`GaussWeight(Hermite(L), L)` は `exp(-Lx²) * H_k(sqrt(L) * x)` によって張られる空間であり、ここで `H_k(x)` はエルミート多項式です。

デフォルトでは、`GaussWeight()` は `GaussWeight(Hermite(), 1.0)` と同等です。
