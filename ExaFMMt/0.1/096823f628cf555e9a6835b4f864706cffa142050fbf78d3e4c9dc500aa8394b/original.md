```
verify(exafmm::ExaFMM{Float32}, fmmoptions::LaplaceFMMOptions{I}) where I
```

Function compute accuracy of evaluated FMM `exafmm`.

# Arguments

  * `exafmmm::ExaFMM{Float32}`: ExaFMM structure with pointers to all allocated variables.
  * `fmmoptions::LaplaceFMMOptions{I}`: Julia Laplace-initializer for setup function, used as identifier.
