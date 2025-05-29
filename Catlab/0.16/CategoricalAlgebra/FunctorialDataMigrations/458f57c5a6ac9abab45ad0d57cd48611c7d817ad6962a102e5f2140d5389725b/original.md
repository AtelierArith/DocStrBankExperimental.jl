Construct a representable C-set.

Recall that a *representable* C-set is one of form $C(c,-): C → Set$ for some object $c ∈ C$.

This function computes the $c$ representable as the left pushforward data migration of the singleton ${c}$-set along the inclusion functor ${c} ↪ C$, which works because left Kan extensions take representables to representables (Mac Lane 1978, Exercise X.3.2). Besides the intrinsic difficulties with representables (they can be infinite), this function thus inherits any limitations of our implementation of left pushforward data migrations.
