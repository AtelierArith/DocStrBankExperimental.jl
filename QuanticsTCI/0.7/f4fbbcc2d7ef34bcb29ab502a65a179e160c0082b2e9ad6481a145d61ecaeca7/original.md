```
function quanticsfouriermpo(
    R::Int;
    sign::Float64=-1.0,
    maxbonddim::Int=12,
    tolerance::Float64=1e-14,
    K::Int=25,
    method::Symbol=:SVD,
    normalize::Bool=true
)::TCI.TensorTrain{ComplexF64}
```

Generate a quantics Fourier transform operator in tensor train form. When contracted with a quantics tensor train $F_{\boldsymbol{\sigma}}$ representing a function, the result will be the fourier transform of the function in quantics tensor train form, $\tilde{F}_{\boldsymbol{\sigma}'} = \sum_{\boldsymbol{\sigma}} F_{\boldsymbol{\sigma}} \exp(-2\pi i (k_{\boldsymbol{\sigma'}}-1) (m_{\boldsymbol{\sigma}} - 1)/M)$, where $k_{\boldsymbol{\sigma}} = \sum_{\ell=1}^R 2^{R-\ell} \sigma_\ell$, $m_{\boldsymbol{\sigma}'} = \sum_{\ell=1}^R 2^{R-\ell} \sigma'_\ell$, and $M=2^R$.

!!! note "Index ordering"
    Before the Fourier transform, the left most index corresponds to $\sigma_1$, which describes the largest length scale, and the right most index corresponds to $\sigma_R$, which describes the smallest length scale. The indices $\sigma_1' \ldots \sigma_{R}'$ in the fourier transformed QTT are aligned in the *inverse* order; that is,  the left most index corresponds to $\sigma'_R$, which describes the smallest length scale. This allows construction of an operator with small bond dimension (see reference 1). If necessary, a call to `TCI.reverse(tt)` can restore large-to-small index ordering.


The Fourier transform operator is implemented using a direct analytic construction of the tensor train by Chen and Lindsey (see reference 2). The tensor train thus obtained is then re-compressed to the user-given bond dimension and tolerance.

Arguments:

  * `R`: number of bits of the fourier transform.
  * `sign`: sign in the exponent $\exp(2i\pi \times \mathrm{sign} \times (k_{\boldsymbol{\sigma'}}-1) (x_{\boldsymbol{\sigma}}-1)/M)$, usually $\pm 1$.
  * `maxbonddim`: bond dimension to compress the operator to. From observations, `maxbonddim = 12` is generally big enough to reach an accuracy of `1e-12`.
  * `tolerance`: tolerance of the TT compression. Note that the error in the fourier transform is generally a bit larger than this error tolerance.
  * `K`: bond dimension of the TT before compression, i.e. number of basis functions to approximate the Fourier transform with (see reference 2). The TT will become inaccurate for `K < 22`; higher values may be necessary for very high precision.
  * `method`: method with which to compress the TT. Choose between `:SVD` and `:CI`.
  * `normalize`: whether or not to normalize the operator as an isometry.

!!! details "References"
    1. [J. Chen, E. M. Stoudenmire, and S. R. White, Quantum Fourier Transform Has Small Entanglement, PRX Quantum 4, 040318 (2023).](https://link.aps.org/doi/10.1103/PRXQuantum.4.040318)
    2. [J. Chen and M. Lindsey, Direct Interpolative Construction of the Discrete Fourier Transform as a Matrix Product Operator, arXiv:2404.03182.](http://arxiv.org/abs/2404.03182)

