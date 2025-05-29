```
chase(I::ACSet, Σ::AbstractDict, n::Int)
```

Chase a C-Set or C-Rel instance given a list of embedded dependencies. This may not terminate, so a bound `n` on the number of iterations is required.

```
[,]
```

ΣS  ⟶ Iₙ ⊕↓      ⋮  (resulting morphism)  ΣT ... Iₙ₊₁

There is a copy of S and T for each active trigger. A trigger is a map from S into the current instance. What makes it 'active' is that there is no morphism from T to I that makes the triangle commute.

Each iteration constructs the above pushout square. The result is a morphism, so that one can keep track of the provenance of elements in the original CSet instance within the chased result.

Whether or not the result is due to success or timeout is returned as a boolean flag.

TODO: this algorithm could be made more efficient by homomorphism caching.
