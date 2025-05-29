```
find_motif(N::T1, m::T2) where {T1<:AbstractEcologicalNetwork, T2<:BinaryNetwork}
```

Returns an array of tuples, in which each tuple contains the species that are part of the motif. The length of the array gives the number of times the motif was found. For probabilistic networks, the tuple also contains the probability of observing the species in the correct conformation for the motif, as well as the variance.

#### References

  * Milo, R., Shen-Orr, S., Itzkovitz, S., Kashtan, N., Chklovskii, D., Alon, U.,

    2002. Network motifs: simple building blocks of complex networks. Science 298,

    824–7. https://doi.org/10.1126/science.298.5594.824
  * Poisot, T., Cirtwill, A.R., Cazelles, K., Gravel, D., Fortin, M.-J., Stouffer, D.B., 2016. The structure of probabilistic networks. Methods in Ecology and Evolution 7, 303–312. https://doi.org/10.1111/2041-210X.12468
