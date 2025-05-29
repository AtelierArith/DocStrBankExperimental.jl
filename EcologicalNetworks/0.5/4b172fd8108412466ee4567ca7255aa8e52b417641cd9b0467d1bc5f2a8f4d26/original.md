```
null3(N::BinaryNetwork; dims::Integer=1)
```

Given a network `N`, `null3(N)` returns a matrix with the same dimensions, where every interaction happens with a probability equal to the out-degree (`dims=1`) or to the in-degree (`dims=2`, number of predecessors) of each species, divided by the total number of possible predecessors/successors.

Note that this does not guarantee that the network is not degenerate, so the output of this analysis *should* be filtered using `is_degenerate`, or passed to `simplify`. The output of this approach is *always* a probabilistic network of the same partiteness as the original network.

#### References

Poisot, T., Stanko, M., Miklisová, D., Morand, S., 2013. Facultative and obligate parasite communities exhibit different network properties. Parasitology 140, 1340–1345. https://doi.org/10.1017/S0031182013000851
