```
Qr(N::T, L::Dict{E,Int64}) where {T<:AbstractEcologicalNetwork,E}
```

Realized modularity – this function returns a value giving the proportion of all links that are within the same module. Higher values reflect a more strongly modular partition (whereas `Q` represents the deviation of modularity from the random expectation).

#### References

  * Poisot, T., 2013. An a posteriori measure of network modularity. F1000Research

    2. https://doi.org/10.12688/f1000research.2-130.v3
