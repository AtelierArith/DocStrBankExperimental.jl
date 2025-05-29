```
cov(f::FiniteGP)
```

`fx`の共分散行列を計算します。

## ノイズのない観測

```jldoctest cov_finitegp
julia> f = GP(Matern52Kernel());

julia> x = randn(11);

julia> cov(f(x)) == kernelmatrix(Matern52Kernel(), x)
true
```

## 等方的観測ノイズ

```jldoctest cov_finitegp
julia> cov(f(x, 0.1)) == kernelmatrix(Matern52Kernel(), x) + 0.1 * I
true
```

## 独立した異方的観測ノイズ

```jldoctest cov_finitegp
julia> s = rand(11);

julia> cov(f(x, s)) == kernelmatrix(Matern52Kernel(), x) + Diagonal(s)
true
```

## 相関した観測ノイズ

```jldoctest cov_finitegp
julia> A = randn(11, 11); S = A'A;

julia> cov(f(x, S)) == kernelmatrix(Matern52Kernel(), x) + S
true
```
