```
null1(N::BinaryNetwork)
```

Given a network `N`, `null1(N)` returns a network with the same dimensions, where every interaction happens with a probability equal to the connectance of `N`.

Note that this does not guarantee that the network is not degenerate, so the output of this analysis *should* be filtered using `is_degenerate`, or passed to `simplify`. The output of this approach is *always* a probabilistic network of the same partiteness as the original network.

#### References

Fortuna, M.A., Bascompte, J., 2006. Habitat loss and the structure of plantanimal mutualistic networks. Ecol. Lett. 9, 281–286. https://doi.org/10.1111/j.1461-0248.2005.00868.x
