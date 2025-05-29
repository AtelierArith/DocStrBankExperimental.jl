```
NFCT{D}
```

A NFCT (nonequispaced fast cosine transform) plan, where D is the dimension. 

The NFCT realizes a direct and fast computation of the discrete nonequispaced cosine transform. The aim is to compute

$$
f^c(\pmb{x}_j) = \sum_{\pmb{k} \in I_{\pmb{N},\mathrm{c}}^D} \hat{f}_{\pmb{k}}^c \, \cos(2\pi \, \pmb{k} \odot \pmb{x}_j)
$$

at given arbitrary knots $\pmb{x}_j \in [0,0.5]^D, j = 1, \cdots, M$, for coefficients $\hat{f}^{c}_{\pmb{k}} \in \mathbb{R}$, $\pmb{k} \in I_{\pmb{N},\mathrm{c}}^D \coloneqq \left\{ \pmb{k} \in \mathbb{Z}^D: 1 \leq k_i \leq N_i - 1, \, i = 1,2,\ldots,D \right\}$, and a multibandlimit vector $\pmb{N} \in \mathbb{N}^{D}$. Note that we define $\cos(\pmb{k} \circ \pmb{x}) \coloneqq \prod_{i=1}^D \cos(k_i \cdot x_i)$. The transposed problem reads as

$$
\hat{h}^c_{\pmb{k}} = \sum_{j=1}^M f^c_j \, \cos(2\pi \, \pmb{k} \odot \pmb{x}_j)
$$

for the frequencies $\pmb{k} \in I_{\pmb{N},\mathrm{c}}^D$ with given coefficients $f^c_j \in \mathbb{R}, j = 1,2,\ldots,M$.

# Fields

  * `N` - the multibandlimit $(N_1, N_2, \ldots, N_D)$ of the trigonometric polynomial $f^s$.
  * `M` - the number of nodes.
  * `n` - the oversampling $(n_1, n_2, \ldots, n_D)$ per dimension.
  * `m` - the window size. A larger m results in more accuracy but also a higher computational cost.
  * `f1` - the NFCT flags.
  * `f2` - the FFTW flags.
  * `init_done` - indicates if the plan is initialized.
  * `finalized` - indicates if the plan is finalized.
  * `x` - the nodes $x_j \in [0,0.5]^D, \, j = 1, \ldots, M$.
  * `f` - the values $f^c(\pmb{x}_j)$ for the NFCT or the coefficients $f_j^c \in \mathbb{R}, j = 1, \ldots, M,$ for the transposed NFCT.
  * `fhat` - the Fourier coefficients $\hat{f}_{\pmb{k}}^c \in \mathbb{R}$ for the NFCT or the values $\hat{h}_{\pmb{k}}^c, \pmb{k} \in I_{\pmb{N},\mathrm{c}}^D,$ for the adjoint NFCT.
  * `plan` - plan (C pointer).

# Constructor

```
NFCT{D}( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32 ) where {D}
```

# Additional Constructor

```
NFCT( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32) where {D}
NFCT( N::NTuple{D,Int32}, M::Int32) where {D}
```

# See also

[`NFCT`](@ref)
