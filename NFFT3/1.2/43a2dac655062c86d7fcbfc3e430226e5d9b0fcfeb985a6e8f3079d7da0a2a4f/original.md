```
NFMT{D}
```

A NFMT (nonequispaced fast mixed transform) plan, where D is the dimension. 

The NFCT realizes a direct and fast computation of the discrete nonequispaced mixed transform. The aim is to compute

$$
f^{\pmb{d}}(\pmb{x}_j) \coloneqq \sum_{\pmb{k} \in I_{\pmb{N},\pmb{d}}^d} \hat{f}_{\pmb{k}}^{\pmb{d}} \, \phi_{\pmb{k}}^{\pmb{d}}(\pmb{x}_j)
$$

with 

$$
\phi_{\pmb{k}}^{\pmb{d}}(\pmb{x})=\prod_{j=1}^d\begin{cases}1,&k_j=0\\\exp(2\pi\mathrm{i}k_jx_j),&d_j=\exp,\;k_j\neq0\\
\sqrt{2}\cos(\pi k_jx_j),&d_j=\cos,\;k_j\neq0\\
\sqrt{2}\cos(k_j\arccos(2x_j-1)),&d_j=\mathrm{alg},\;k_j\neq0\end{cases}
$$

for $\pmb{d}\in\{\exp,\cos,\mathrm{alg}\}^d$ at given arbitrary knots $\pmb{x}_j \in [0,1]^D, j = 1, \cdots, M$, for coefficients $\hat{f}^{c}_{\pmb{k}} \in \mathbb{R}$, 

$$
\pmb{k}\inI_{\pmb{N},\pmb{d}}^d \coloneqq \overset{d}{\underset{j=1}{\vphantom{\mathop{\raisebox{-.5ex}{\hbox{\huge{$\times$}}}}}⨉}}\begin{cases}\Big\{-\frac{N_j}{2},-\frac{N_j}{2}+1,\ldots,\frac{N_j}{2}\Big\},&d_j=\exp\\\Big\{0,1,\ldots,\frac{N_j}{2}\Big\},&d_j\neq\exp\end{cases},
$$

and a multibandlimit vector $\pmb{N} \in (2\mathbb{N})^{D}$. The transposed problem reads as

$$
\hat{h}^{\pmb{d}}_{\pmb{k}} = \sum_{j=1}^M f^{\pmb{d}}_j \, \phi_{\pmb{k}}^{\pmb{d}}(\pmb{x}_j)
$$

for the frequencies $\pmb{k} \in I_{\pmb{N},\pmb{d}}^D$ with given coefficients $f^{\pmb{d}}_j \in \mathbb{R}, j = 1,2,\ldots,M$.

# Fields

  * `basis_vect` - tuple with the bases (`exp`, `cos`, `alg`) for each dimension
  * `NFFT_struct` - underlying [NFFT plan](@ref NFFT_site# Plan structure).

# Constructor

```
NFMT{D}( basis_vect::NTuple{D,String}, P::NFFT{D}N::NTuple{D,Int32}) where {D}
```

> **WARNING**: Not for direct usage!


# Additional Constructor

```
NFMT( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32) where {D}
NFMT( N::NTuple{D,Int32}, M::Int32) where {D}
```

with

  * `N` - the multibandlimit $(N_1, N_2, \ldots, N_D)$ of the trigonometric polynomial $f^s$.
  * `M` - the number of nodes.
  * `n` - the oversampling $(n_1, n_2, \ldots, n_D)$ per dimension.
  * `m` - the window size. A larger m results in more accuracy but also a higher computational cost.
  * `f1` - the NFST flags.
  * `f2` - the FFTW flags.

# See also

[NFMT`](@ref)
