```
verify(exafmm::ExaFMM{ComplexF32}, fmmoptions::HelmholtzFMMOptions{I, ComplexF32}) where I
```

Function compute accuracy of evaluated FMM `exafmm`.

# Arguments

  * `exafmmm::ExaFMM`: ExaFMM structure with pointers to all allocated variables.
  * `fmmoptions::HelmholtzFMMOptions{I, ComplexF32}`: Julia Helmoltz-initializer for setup function, used as identifier.
