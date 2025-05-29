Transformation between C-sets.

Recall that a C-set homomorphism is a natural transformation: a transformation between functors C → Set satisfying the naturality axiom for every morphism, or equivalently every generating morphism, in C.

This data type records the data of a C-set transformation. Naturality is not strictly enforced but is expected to be satisfied. It can be checked using the function [`is_natural`](@ref).

If the schema of the dom and codom has attributes, this has the semantics of  being a valid C-set transformation on the combinatorial data alone (including  attribute variables, if any).
