```
NFFT{D}
```

A NFFT (nonequispaced fast Fourier transform) plan, where D is the dimension. 

Considering a D-dimensional trigonometric polynomial

$$
f \colon \mathbb{T}^D \to \mathbb{C}, \; f(\pmb{x}) \colon = \sum_{\pmb{k} \in I_{\pmb{N}}^D} \hat{f}_{\pmb{k}} \, \mathrm{e}^{-2 \pi \mathrm{i} \, \pmb{k} \cdot \pmb{x}}
$$

with an index set $I_{\pmb{N}}^D \coloneqq \left\{ \pmb{k} \in \mathbb{Z}^D: - \frac{N_i}{2} \leq k_i \leq \frac{N_i}{2} - 1, \, i = 1,2,\ldots,D \right\}$ where $\pmb{N} \in (2\mathbb{N})^{D}$ is the multibandlimit.  The NDFT (nonequispaced discrete Fourier transform) is its evaluation at $M \in \mathbb{N}$ arbitrary points $\pmb{x}_j \in [-0.5,0.5)^D$ for $j = 1, \ldots, M$,

$$
f(\pmb{x}_j) \colon = \sum_{\pmb{k} \in I^D_{\pmb{N}}} \hat{f}_{\pmb{k}} \, \mathrm{e}^{-2 \pi \mathrm{i} \, \pmb{k} \cdot \pmb{x}_j}
$$

with given coefficients $\hat{f}_{\pmb{k}} \in \mathbb{C}$. The NFFT is an algorithm for the fast evaluation of the NDFT and the adjoint problem, the fast evaluation of the adjoint NDFT

$$
\hat{h}_{\pmb{k}} \coloneqq \sum^{M}_{j = 1} f_j \, \mathrm{e}^{-2 \pi \mathrm{i} \, \pmb{k} \cdot \pmb{x}_j}, \, \pmb{k} \in I_{\pmb{N}}^D,
$$

for given coefficients $f_j \in \mathbb{C}, j =1,2,\ldots,M$. Note that in general, the adjoint NDFT is not the inverse transform of the NDFT.

# Fields

  * `N` - the multibandlimit $(N_1, N_2, \ldots, N_D)$ of the trigonometric polynomial $f$.
  * `M` - the number of nodes.
  * `n` - the oversampling $(n_1, n_2, \ldots, n_D)$ per dimension.
  * `m` - the window size. A larger m results in more accuracy but also a higher computational cost.
  * `f1` - the NFFT flags.
  * `f2` - the FFTW flags.
  * `init_done` - indicates if the plan is initialized.
  * `finalized` - indicates if the plan is finalized.
  * `x` - the nodes $\pmb{x}_j \in [-0.5,0.5)^D, j = 1, \ldots, M$.
  * `f` - the values $f(\pmb{x}_j)$ for the NFFT or the coefficients $f_j \in \mathbb{C}, j = 1, \ldots, M,$ for the adjoint NFFT.
  * `fhat` - the Fourier coefficients $\hat{f}_{\pmb{k}} \in \mathbb{C}$ for the NFFT or the values $\hat{h}_{\pmb{k}}, \pmb{k} \in I_{\pmb{N}}^D,$ for the adjoint NFFT.
  * `plan` - plan (C pointer).

# Constructor

```
NFFT{D}( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32 ) where D
```

# Additional Constructor

```
NFFT( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32 ) where {D}
NFFT( N::NTuple{D,Int32}, M::Int32 ) where {D}
```
