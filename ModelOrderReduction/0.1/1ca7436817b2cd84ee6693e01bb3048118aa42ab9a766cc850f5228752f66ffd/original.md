```julia
deim(
    full_vars,
    linear_coeffs,
    constant_part,
    nonlinear_part,
    reduced_vars,
    linear_projection_matrix,
    nonlinear_projection_matrix;
    kwargs...
)

```

Compute the reduced model by applying the Discrete Empirical Interpolation Method (DEIM).

This method allows users to input the projection matrices of their own choices.

Given the projection matrix $V\in\mathbb R^{n\times k}$ for the dependent variables $\mathbf y\in\mathbb R^n$ and the projection matrix $U\in\mathbb R^{n\times m}$ for the nonlinear function $\mathbf F\in\mathbb R^n$, the full-order model (FOM)

$$
\frac{d}{dt}\mathbf y(t)=A\mathbf y(t)+\mathbf g(t)+\mathbf F(\mathbf y(t))
$$

is transformed to the reduced-order model (ROM)

$$
\frac{d}{dt}\hat{\mathbf y}(t)=\underbrace{V^TAV}_{k\times k}\hat{\mathbf y}(t)+V^T
\mathbf g(t)+\underbrace{V^TU(P^TU)^{-1}}_{k\times m}\underbrace{P^T\mathbf F(V
\hat{\mathbf y}(t))}_{m\times1}
$$

where $P=[\mathbf e_{\rho_1},\dots,\mathbf e_{\rho_m}]\in\mathbb R^{n\times m}$, $\rho_1,\dots,\rho_m$ are interpolation indices from the DEIM point selection algorithm, and $\mathbf e_{\rho_i}=[0,\ldots,0,1,0,\ldots,0]^T\in\mathbb R^n$ is the $\rho_i$-th column of the identity matrix $I_n\in\mathbb R^{n\times n}$.

# Arguments

  * `full_vars::AbstractVector`: the dependent variables $\underset{n\times 1}{\mathbf y}$ in FOM.
  * `linear_coeffs::AbstractMatrix`: the coefficient matrix $\underset{n\times n}A$ of linear terms in FOM.
  * `constant_part::AbstractVector`: the constant terms $\underset{n\times 1}{\mathbf g}$ in FOM.
  * `nonlinear_part::AbstractVector`: the nonlinear functions $\underset{n\times 1}{\mathbf F}$ in FOM.
  * `reduced_vars::AbstractVector`: the dependent variables $\underset{k\times 1}{\hat{\mathbf y}}$ in the reduced-order model.
  * `linear_projection_matrix::AbstractMatrix`: the projection matrix $\underset{n\times k}V$ for the dependent variables $\mathbf y$.
  * `nonlinear_projection_matrix::AbstractMatrix`: the projection matrix $\underset{n\times m}U$ for the nonlinear functions $\mathbf F$.

# Return

  * `reduced_rhss`: the right hand side of ROM.
  * `linear_projection_eqs`: the linear projection mapping $\mathbf y=V\hat{\mathbf y}$.
