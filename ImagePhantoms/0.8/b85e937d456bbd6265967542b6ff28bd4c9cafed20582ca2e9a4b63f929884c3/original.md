mri*smap*basis(mask ; kmax, kt, ki)

Construct Fourier basis for representing MRI sensitivity maps in terms of separable complex exponential signals, products of of the form `basis = (k,N) -> exp.(2im * π * nfun(N) * kfun(k,N))`. The default is `nfun(N) = -(N÷2):(N÷2)-1` which is suitable for even `N` only. The default is `kfun(k,N) = k / 2N`, which is DCT-II like frequencies, leading to better boundary behavior than the DFT frequencies `k/N`.

# Input

  * `mask::AbstractArray{Bool,D}` binary support mask for region to reconstruct

# Option

  * `kmax::Int = 5` default frequency index -kmax:kmax in all dimensions
  * `kfun::Function = (k,N) -> k / (2N)` # DCT-II frequency
  * `deltas::NTuple{D,<:Number} = ones(D)` pixel sizes

(For additional options `kmaxs`, `kt`, `ki`, `T`, see code.)

# Output

  * `(; B, ν)` where `B` is basis matrix of size `count(mask) × nk` where typically `nk = (2*kmax+1)^D` and `ν` is `nk` frequency tuples; each tuple has form `ν = kfun.(Tuple(k), size(mask)) ./ deltas`.
