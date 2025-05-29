```
isdetailedbalanced(rs::ReactionSystem, parametermap; reltol=1e-9, abstol)
```

Constructively compute whether a kinetic system (a reaction network with a set of rate constants) will admit detailed-balanced equilibrium solutions, using the Wegscheider conditions, [Feinberg, 1989](https://www.sciencedirect.com/science/article/pii/0009250989851243). A detailed-balanced solution is one for which the rate of every forward reaction exactly equals its reverse reaction. Accepts a dictionary, vector, or tuple of variable-to-value mappings, e.g. [k1 => 1.0, k2 => 2.0,...].
