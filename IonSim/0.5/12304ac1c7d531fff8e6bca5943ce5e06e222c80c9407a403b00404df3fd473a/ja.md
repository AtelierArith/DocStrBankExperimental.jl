```
basis(chain::LinearChain)::CompositeBasis
```

`chain`のヒルベルト空間を記述する複合基底を返します。

順序は $ion₁ ⊗ ion₂ ⊗ ... ⊗ ion_N ⊗ mode₁ ⊗ mode₂ ⊗ ... ⊗ mode_N$ であり、イオン基底は `ions(chain)` の順序に従って並べられ、振動モードは `[xmodes(chain), ymodes(chain), zmodes(chain)]` の順序に従って並べられます。
