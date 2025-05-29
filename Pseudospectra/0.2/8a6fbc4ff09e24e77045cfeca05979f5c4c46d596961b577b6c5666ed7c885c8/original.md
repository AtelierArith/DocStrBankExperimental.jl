```
spectralportrait(A::AbstractMatrix; npts=100) => Plots object
```

compute pseudospectra of matrix `A` and display as a spectral portrait.

Pseudospectra are computed on a grid of `npts` by `npts` points in the complex plane, including a neighborhood of the spectrum. Contour levels are `log10(ϵ)` where `ϵ` is the inverse resolvent norm. This is a convenience wrapper for simple cases; see the Pseudospectra package documentation for more elaborate interfaces.
