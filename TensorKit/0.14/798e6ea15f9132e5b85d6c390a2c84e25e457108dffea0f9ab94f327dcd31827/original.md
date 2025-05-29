```
⊠(V₁::VectorSpace, V₂::VectorSpace)
```

Given two vector spaces `V₁` and `V₂` (`ElementarySpace` or `ProductSpace`), or thus, objects of corresponding fusion categories $C₁$ and $C₂$, $V₁ ⊠ V₂$ constructs the Deligne tensor product, an object in $C₁ ⊠ C₂$ which is the natural tensor product of those categories. In particular, the corresponding type of sectors (simple objects) is given by `sectortype(V₁ ⊠ V₂) == sectortype(V₁) ⊠ sectortype(V₂)` and can be thought of as a tuple of the individual sectors.

The Deligne tensor product also works in the type domain and for sectors and tensors. For group representations, we have `Rep[G₁] ⊠ Rep[G₂] == Rep[G₁ × G₂]`, i.e. these are the natural representation spaces of the direct product of two groups.
