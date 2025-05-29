```
normalize_eigenmode!(evec_pair, eval_pair, phase_mode::Integer=-1)
```

Normalizes the complex-conjugate eigenvector pair so that `vⱼ'*S*vⱼ = +im`  for `j=1`, and `-im` for `j=2`. This may involve swapping the complex-conjugate  eigenvectors/eigenvalues.

If `phase_mode` is set to a particular mode (1, 2, 3), then a phase will be multiplied by the  eigenvectors to make them "pretty"; the phase will make the first component of that mode (e.g.  the x, y, or z component) be fully real. This gives the eigenvectors a simple form in the  weakly-coupled case, with the product `v₁'*v₂` having a positive imaginary part, and ensures the  odd numbered eigenvector/eigenvalues are associated with the tune and the even numbered ones have  the negative of the tune. In cases with a lot of coupling, there is no simple way to define the  positive or negative tune, and multiplying by this phase factor is harmless. See the "Tunes From  One-Turn Matrix Eigen Analysis" section in the Bmad manual for more details. 
