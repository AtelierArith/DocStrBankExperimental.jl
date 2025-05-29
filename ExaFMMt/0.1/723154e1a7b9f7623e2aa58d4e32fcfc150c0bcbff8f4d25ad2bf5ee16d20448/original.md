```
verify(exafmm::ExaFMM{ComplexF64}, fmmoptions::HelmholtzFMMOptions{I, ComplexF64}) where I
```

Function compute accuracy of evaluated FMM `exafmm`.

# Arguments

  * `exafmmm::ExaFMM`: ExaFMM structure with pointers to all allocated variables.
  * `fmmoptions::HelmholtzFMMOptions{I, ComplexF64}`: Julia Helmoltz-initializer for setup function, used as identifier.
