A span homomorphism is a homomorphism between apexes and isomorphisms between the feet of the span. This function is a work in progress.

```
   X
↙  |  ↘
```

X₁   |    X₂ ≅ ↓    |    ↓ ≅   Y₁   |    Y₂     ↖  v  ↗        Y

TODO: this isn't implemented correctly, currently, for two reasons.

1. We need to search over all possible combinations of isomorphisms among the legs, as opposed to just picking an arbitrary one.
2. Each part of X maps to a part in Yₙ for each n. The preimage along Y's leg #n gives a set of acceptable values that this part of X can map to. The code currently stops if there is any preimage that has more than one element (because this is a constraint that has already been implemented in homomorphism search) but to be correct we must implement search where each x∈X can be designated a list of allowable values in Y to map to.

The relevance of this code being in this repo is that it seems likely that CSetAutomorphisms can help us avoid the combinatorial explosion of searching over all combinations of isomorphisms between the pairs of legs. It is not as simple as converting each of the leg C-Sets into canonical form: imagine x₁ ↦ y₁₁ and y₁↦ y₁₂ ... ignoring isomorphisms, it would seem like we cannot map x₁ ↦ y₁. However, if y₁₁ and y₁₂ are in the same *orbit*, then there does exist an isomorphism that would allow us to do this mapping. The challenge is when we then continue for x₂, etc. We've actually broken some symmetry by distinguishing y₁₁. But it seems like color saturation would allow us to break whatever orbits are broken by this distinction and then continue in the same way with the rest of the elements in X. This is future work.
