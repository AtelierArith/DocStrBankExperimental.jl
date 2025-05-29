```
SpinWaveTheoryKPM(sys::System; measure, regularization=1e-8, tol=nothing,
                  niters=nothing, niters_bounds=10, method=:lanczos)
```

A variant of [`SpinWaveTheory`](@ref) that estimates [`intensities`](@ref) using iterated matrix-vector products. By avoiding direct matrix diagonalization, this method reduces computational cost from cubic to linear-scaling in the system size $N$. Large system sizes can arise, e.g., for models of quenched disorder or models with nearly incommensurate ordering wavevectors.

Computational cost scales like $𝒪(N M + M^2)$. The number of iterations $M$ may be specified directly with the `niters` parameter. Alternatively, one may specify a dimensionless error tolerance `tol` such that `M ≈ -2 log10(tol) Δϵ / fwhm` where `Δϵ` is the estimated spectral bandwidth of excitations and `fwhm` is the full width at half maximum of the user-supplied broadening `kernel`. Common choices for `tol` are `0.05` (more speed) or `0.01` (more accuracy). Either `tol` or `niters` is required. The parameter `niters_bounds` selects the Krylov subspace dimension to be used for estimating spectral bounds.

!!! warning "Accuracy considerations"
    Energy-space resolution scales inversely with the number $M$ of iterations. Such broadening errors can usually be well controlled via the tolerance parameter `tol`. A more serious problem is intensity loss at bands with small excitation energy, e.g., in the viscinity of Goldstone modes. In certain cases this missing intensity will be due to numerical roundoff error that cannot be fixed by increasing the number of iterations $M$.


Two `method` options are available, `:lanczos` and `:kpm`.  Lanczos is generally preferred, as it achieves near-optimal accuracy for a given number of iterations [1, 2]. The Lanczos implementation builds on earlier research using the Kernel Polynomial Method [3], which may be of historical interest.

## References

1. [T. Chen, *The Lanczos algorithm for matrix functions: a handbook for scientists* (2024) [arXiv:2410.11090]](https://arxiv.org/abs/2410.11090).
2. [N. Amsel, T. Chen, A. Greenbaum, C. Musco, C. Musco, *Near-Optimal Approximation of Matrix Functions by the Lanczos Method* (2023) [arXiv:2303.03358]](https://arxiv.org/abs/2303.03358).
3. [H. Lane et al., *Kernel Polynomial Method for Linear Spin Wave Theory* (2023) [arXiv:2312.08349]](https://arxiv.org/abs/2312.08349).
