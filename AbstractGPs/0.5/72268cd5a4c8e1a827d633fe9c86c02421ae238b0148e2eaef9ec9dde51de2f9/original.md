```
cov(f::FiniteGP)
```

Compute the covariance matrix of `fx`.

## Noise-free observations

```jldoctest cov_finitegp
julia> f = GP(Matern52Kernel());

julia> x = randn(11);

julia> cov(f(x)) == kernelmatrix(Matern52Kernel(), x)
true
```

## Isotropic observation noise

```jldoctest cov_finitegp
julia> cov(f(x, 0.1)) == kernelmatrix(Matern52Kernel(), x) + 0.1 * I
true
```

## Independent anisotropic observation noise

```jldoctest cov_finitegp
julia> s = rand(11);

julia> cov(f(x, s)) == kernelmatrix(Matern52Kernel(), x) + Diagonal(s)
true
```

## Correlated observation noise

```jldoctest cov_finitegp
julia> A = randn(11, 11); S = A'A;

julia> cov(f(x, S)) == kernelmatrix(Matern52Kernel(), x) + S
true
```
