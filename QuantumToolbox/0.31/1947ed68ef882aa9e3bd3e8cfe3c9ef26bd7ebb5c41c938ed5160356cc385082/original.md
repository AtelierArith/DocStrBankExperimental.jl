```
coherent(N::Int, α::Number)
```

Generates a [coherent state](https://en.wikipedia.org/wiki/Coherent_state) $|\alpha\rangle$, which is defined as an eigenvector of the bosonic annihilation operator $\hat{a} |\alpha\rangle = \alpha |\alpha\rangle$.

This state is constructed via the displacement operator [`displace`](@ref) and zero-fock state [`fock`](@ref): $|\alpha\rangle = \hat{D}(\alpha) |0\rangle$
