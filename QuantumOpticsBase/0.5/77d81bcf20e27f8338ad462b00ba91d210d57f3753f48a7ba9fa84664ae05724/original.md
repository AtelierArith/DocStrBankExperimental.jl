```
manybodyoperator(mb::ManyBodyBasis, op)
```

Create the many-body operator from the given one-body operator `op`.

The given operator can either be a one-body operator or a two-body interaction. Higher order interactions are at the moment not implemented.

The mathematical formalism for the one-body case is described by

$$
X = \sum_{ij} a_i^† a_j ⟨u_i| x | u_j⟩
$$

and for the interaction case by

$$
X = \sum_{ijkl} a_i^† a_j^† a_k a_l ⟨u_i|⟨u_j| x |u_k⟩|u_l⟩
$$

where $X$ is the N-particle operator, $x$ is the one-body operator and $|u⟩$ are the one-body states associated to the different modes of the N-particle basis.
