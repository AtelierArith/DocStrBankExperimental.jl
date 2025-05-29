The HCubature module is a pure-Julia implementation of multidimensional "h-adaptive" integration.  That is, given an n-dimensional integral

$\int_{a_1}^{b_1}\int_{a_2}^{b_2}\cdots\int_{a_n}^{b_n} (\vec{x}) d^n\vec{x}$

then `hcubature(f, a, b)` computes the integral, adaptively subdividing the integration volume into smaller and smaller pieces until convergence is achieved to the desired tolerance (specified by optional `rtol` and `atol` keyword arguments, described in more detail below.

Because `hcubature` is written purely in Julia, the integrand `f(x)` can return any vector-like object (technically, any type supporting `+`, `-`, `*` real, and `norm`: a Banach space).  You can integrate real, complex, and matrix-valued integrands, for example.
