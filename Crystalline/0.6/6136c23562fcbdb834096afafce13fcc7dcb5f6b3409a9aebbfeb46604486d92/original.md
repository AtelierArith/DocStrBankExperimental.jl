```
basisdim(brs::BandRepSet) --> Int
```

Return the dimension of the (linearly independent parts) of a band representation set. This is $d^{\text{bs}} = d^{\text{ai}}$ in the notation of [Po, Watanabe, & Vishwanath, Nature Commun. **8**, 50 (2017)](https://doi.org/10.1038/s41467-017-00133-2), or  equivalently, the rank of `stack(brs)` over the ring of integers. This is the number of linearly independent basis vectors that span the expansions of a band structure viewed as symmetry data.
