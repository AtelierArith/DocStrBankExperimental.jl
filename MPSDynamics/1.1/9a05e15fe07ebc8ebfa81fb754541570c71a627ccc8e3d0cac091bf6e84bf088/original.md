```
xyzmpo(N::Int; Jx=1.0, Jy=Jx, Jz=Jx, hx=0., hz=0.)
```

Generate MPO for the `N`-spin XYZ model with external field $\vec{h}=(h_x, 0, h_z)$, , defined by the Hamiltonian

$H = \sum_{n=1}^{N-1} -J_x σ_x^{n} σ_x^{n+1} - J_y σ_y^{n} σ_y^{n+1} - J_z σ_z^{n} σ_z^{n+1} + \sum_{n=1}^{N}(- h_x σ_x^{n} - h_z σ_z^{n})$

with $σ_x^{n}, σ_y^{n}, σ_z^{n}$ the Pauli spin-1/2 matrices of the $n^\text{th}$ site.
