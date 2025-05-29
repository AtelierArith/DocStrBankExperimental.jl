```
⊠(s₁::Sector, s₂::Sector)
deligneproduct(s₁::Sector, s₂::Sector)
```

Given two sectors `s₁` and `s₂`, which label an isomorphism class of simple objects in a fusion category $C₁$ and $C₂$, `s1 ⊠ s2` (obtained as `\boxtimes+TAB`) labels the isomorphism class of simple objects in the Deligne tensor product category $C₁ ⊠ C₂$.

The Deligne tensor product also works in the type domain and for spaces and tensors. For group representations, we have `Irrep[G₁] ⊠ Irrep[G₂] == Irrep[G₁ × G₂]`.
