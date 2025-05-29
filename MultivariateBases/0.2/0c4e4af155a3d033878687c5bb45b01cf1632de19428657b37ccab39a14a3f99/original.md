```
struct ScaledMonomialBasis{MT<:MP.AbstractMonomial, MV<:AbstractVector{MT}} <: AbstractPolynomialBasis
    monomials::MV
end
```

*Scaled monomial basis* (see [Section 3.1.5, BPT12]) with the monomials of the vector `monomials`. Given a monomial $x^\alpha = x_1^{\alpha_1} \cdots x_n^{\alpha_n}$ of degree $d = \sum_{i=1}^n \alpha_i$, the corresponding polynomial of the basis is

$$
{d \choose \alpha}^{\frac{1}{2}} x^{\alpha} \quad \text{ where } \quad
{d \choose \alpha} = \frac{d!}{\alpha_1! \alpha_2! \cdots \alpha_n!}.
$$

For instance, create a polynomial with the basis $[xy^2, xy]$ creates the polynomial $\sqrt{3} a xy^2 + \sqrt{2} b xy$ where `a` and `b` are new JuMP decision variables. Constraining the polynomial $axy^2 + bxy$ to be zero with the scaled monomial basis constrains `a/√3` and `b/√2` to be zero.

This basis is orthonormal under the scalar product:

$$
\langle f, g \rangle = \int_{\mathcal{C}^n} f(z) \overline{g(z)} d\nu_n
$$

where $\nu_n$ is the Gaussian measure on $\mathcal{C}^n$ with the density $\pi^{-n} \exp(-\lVert z \rVert^2)$. See [Section 4; B07] for more details.

[BPT12] Blekherman, G.; Parrilo, P. A. & Thomas, R. R. *Semidefinite Optimization and Convex Algebraic Geometry*. Society for Industrial and Applied Mathematics (2012).

[B07] Barvinok, Alexander. *Integration and optimization of multivariate polynomials by restriction onto a random subspace.* Foundations of Computational Mathematics 7.2 (2007): 229-244.
