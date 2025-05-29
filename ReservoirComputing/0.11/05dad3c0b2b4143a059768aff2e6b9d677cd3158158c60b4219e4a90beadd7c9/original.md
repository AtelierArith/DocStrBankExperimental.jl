```
RandomMapping(permutations, expansion_size)
RandomMapping(permutations; expansion_size=40)
RandomMapping(;permutations=8, expansion_size=40)
```

Random mapping of the input data directly in the reservoir. The `expansion_size` determines the dimension of the single reservoir, and `permutations` determines the number of total reservoirs that will be connected, each with a different mapping. The detail of this implementation can be found in [1].

[1] Nichele, Stefano, and Andreas Molund. “Deep reservoir computing using cellular automata.” arXiv preprint arXiv:1703.02806 (2017).
