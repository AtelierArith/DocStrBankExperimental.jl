```
FASTSUM
```

The fast summation algorithm evaluates the function

$$
f(\pmb{y}) \coloneqq \sum^{N}_{k = 1} \alpha_k \, \mathscr{K}(\pmb{y} - \pmb{x}_k) = \sum^{N}_{k = 1} \alpha_k \, K(\lVert \pmb{y} - \pmb{x}_k \rVert_2)
$$

for given arbitrary source knots $\pmb{x}_k \in \mathbb{R}^d, k = 1,2, \cdots, N$ and a given kernel function $\mathscr{K}(\cdot) = K (\lVert \cdot \rVert_2), \; \pmb{x} \in \mathbb{R}^d$,  which is an even, real univariate function which is infinitely differentiable at least in $\mathbb{R} \setminus \{ 0 \}$.  If $K$ is infinitely differentiable at zero as well, then $\mathscr{K}$ is defined on $\mathbb{R}^d$ and is called  nonsingular kernel function. The evaluation is done at $M$ different points $\pmb{y}_j \in \mathbb{R}^d, j = 1, \cdots, M$. 

# Fields

  * `d` - dimension.
  * `N` - number of source nodes.
  * `M` - number of target nodes.
  * `n` - expansion degree.
  * `p` - degree of smoothness.
  * `kernel` - name of kernel function $K$, see [Supported kernel functions](# Supported kernel functions).
  * `c` - kernel parameters.
  * `eps_I` - inner boundary.
  * `eps_B` - outer boundary.
  * `nn_x` - oversampled nn in x.
  * `nn_y` - oversampled nn in y.
  * `m_x` - NFFT-cutoff in x.
  * `m_y` - NFFT-cutoff in y.
  * `init_done` - bool for plan init.
  * `finalized` - bool for finalizer.
  * `flags` - flags.
  * `x` - source nodes with $\lVert \pmb{x}_k \rVert_2 \leq \frac{1}{2} \ (\frac{1}{2} - \varepsilon_B)$.
  * `y` - target nodes with $\lVert \pmb{y}_k \rVert_2 \leq \frac{1}{2} \ (\frac{1}{2} - \varepsilon_B)$.
  * `alpha` - source coefficients.
  * `f` - target evaluations.
  * `plan` - plan (C pointer).

# Constructor

```
FASTSUM( d::Integer, N::Integer, M::Integer, n::Integer, p::Integer, kernel::String, c::Vector{<:Real}, eps_I::Real, eps_B::Real, nn_x::Integer, nn_y::Integer, m_x::Integer, m_y::Integer, flags::UInt32 )
```

# Additional Constructor

```
FASTSUM( d::Integer, N::Integer, M::Integer, n::Integer, p::Integer, kernel::String, c::Real, eps_I::Real, eps_B::Real, nn::Integer, m::Integer )
```

# See also

[`NFFT`](@ref)
