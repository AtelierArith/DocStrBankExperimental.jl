```
inner(ω, ξ)
```

Usual inner product between [`Cochain`](@ref)s.

!!! warning
    For complex Cochains, the conjugation is taken on the **first** entry.


This inner product sees a n-cochain as a free vector space over the (non-oriented) n-simplices of their base space. Formally,

$$
\sum_{\sigma \in \mathrm{simplices}(K,n)} \overline{f(σ)} g(σ).
$$
