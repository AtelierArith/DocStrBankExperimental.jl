```
verify(exafmm::ExaFMM{Float64}, fmmoptions::ModifiedHelmholtzFMMOptions{I, Float64})
```

Function compute accuracy of evaluated FMM `exafmm`.

# Arguments

  * `exafmmm::ExaFMM{Float64}`: ExaFMM structure with pointers to all allocated variables.
  * `fmmoptions::ModifiedHelmholtzFMMOptions{I, Float64}`: Julia modified-Helmholtz-initializer for setup function, used as identifier.
