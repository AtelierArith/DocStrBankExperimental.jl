```
mat_eigen(mat; sort=true, phase_modes=true)
```

Given a matrix `mat` with an even number of rows/cols, calculates the eigenvectors  and eigenvalues. For stable eigenmodes (complex conjugate eigenvector/eigenvalue pairs),  the eigenvectors are normalized so that `vⱼ'*S*vⱼ = +im` for odd `j`, and `-im` for even `j`.

If `sort` is true, then each eigenvector/eigenvalue pair will be sorted according to the mode  it best identifies with. A warning will be printed if the mode sorting fails. Mode sorting  will automatically fail if more than 1 mode is unstable. Default is true.

If `phase_modes` is true, then each stable mode will be multiplied by a phase factor to make  the first component of that mode (e.g. the x, y, or z component, NOT the px, py, or pz component)  be fully real. This both makes the eigenvector "pretty", and in this case of weak coupling, ensures  that `vⱼ'*vⱼ₊₁` for j=(1, 3, 5) has a positive imaginary part so that the eigenvectors/eigenvalues  for odd `j` are associated with the positive tune and even `j` the negative tune. This  phase factor is harmless/useless to include in a highly-coupled matrix.

For complex matrices, Julia's `eigen`, which is called by `mat_eigen`, is type-unstable.
