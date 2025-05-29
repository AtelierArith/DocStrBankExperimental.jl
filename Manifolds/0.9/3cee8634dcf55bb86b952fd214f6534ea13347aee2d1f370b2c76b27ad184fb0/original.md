```
exp(M::Grassmann, p::ProjectorPoint, X::ProjectorTVector)
```

Compute the exponential map on the [`Grassmann`](@ref) as

$$
    \exp_pX = \operatorname{Exp}([X,p])p\operatorname{Exp}(-[X,p]),
$$

where $\operatorname{Exp}$ denotes the matrix exponential and $[A,B] = AB-BA$ denotes the matrix commutator.

For details, see Proposition 3.2 in [BendokatZimmermannAbsil:2020](@cite).
