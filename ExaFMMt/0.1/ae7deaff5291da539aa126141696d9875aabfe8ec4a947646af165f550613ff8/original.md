```
verify(exafmm::ExaFMM{Float32}, fmmoptions::ModifiedHelmholtzFMMOptions{I, Float32})
```

Function compute accuracy of evaluated FMM `exafmm`.

# Arguments

  * `exafmmm::ExaFMM{Float32}`: ExaFMM structure with pointers to all allocated variables.
  * `fmmoptions::ModifiedHelmholtzFMMOptions{I, Float32}`: Julia modified-Helmholtz-initializer for setup function, used as identifier.
