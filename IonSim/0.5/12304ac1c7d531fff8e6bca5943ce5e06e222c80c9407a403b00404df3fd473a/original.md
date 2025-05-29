```
basis(chain::LinearChain)::CompositeBasis
```

Returns the composite basis describing the Hilbert space for `chain`.

Order is $ion₁ ⊗ ion₂ ⊗ ... ⊗ ion_N ⊗ mode₁ ⊗ mode₂ ⊗ ... ⊗ mode_N$, where the ion bases are ordered according to the order in `ions(chain)` and the vibrational modes are ordered according to the order in `[xmodes(chain), ymodes(chain), zmodes(chain)]`.
