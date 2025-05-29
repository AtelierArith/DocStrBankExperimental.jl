```
null2(N::BinaryNetwork)
```

Given a network `N`, `null2(N)` returns a network with the same dimensions, where every interaction happens with a probability equal to the degree of each species.

Note that this does not guarantee that the network is not degenerate, so the output of this analysis *should* be filtered using `is_degenerate`, or passed to `simplify`. The output of this approach is *always* a probabilistic network of the same partiteness as the original network.

#### References

Bascompte, J., Jordano, P., Melian, C.J., Olesen, J.M., 2003. The nested assembly of plant-animal mutualistic networks. PNAS 100, 9383–9387. https://doi.org/10.1073/pnas.1633576100
