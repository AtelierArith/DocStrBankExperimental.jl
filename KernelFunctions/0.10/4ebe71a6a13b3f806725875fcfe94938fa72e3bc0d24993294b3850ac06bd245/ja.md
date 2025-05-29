```
spectral_mixture_kernel(
    h::Kernel=SqExponentialKernel(),
    αs::AbstractVector{<:Real},
    γs::AbstractMatrix{<:Real},
    ωs::AbstractMatrix{<:Real},
)
```

ここで、αsは次元(A, )の重み、γsは次元(D, A)の共分散行列、ωsは次元(D, A)の平均ベクトルです。ここで、Dは入力次元、Aはスペクトル成分の数です。

`h`はカーネルで、指定されていない場合は[`SqExponentialKernel`](@ref)がデフォルトとなります。

!!! warning
    コンストラクタが型安定であることを確認したい場合は、[`StaticArrays`](https://github.com/JuliaArrays/StaticArrays.jl)の引数を提供する必要があります：`αs`は`StaticVector`、`γs`と`ωs`は`StaticMatrix`として。


一般化されたスペクトル混合カーネル関数。この関数のファミリーは、点ごとの収束に関して定常実数値カーネルのファミリーにおいて密です。[1]

$$
   κ(x, y) = αs' (h(-(γs' * t)^2) .* cos(π * ωs' * t), t = x - y
$$

# 参考文献:

```
[1] Generalized Spectral Kernels, by Yves-Laurent Kom Samo and Stephen J. Roberts
[2] SM: Gaussian Process Kernels for Pattern Discovery and Extrapolation,
        ICML, 2013, by Andrew Gordon Wilson and Ryan Prescott Adams,
[3] Covariance kernels for fast automatic pattern discovery and extrapolation
    with Gaussian processes, Andrew Gordon Wilson, PhD Thesis, January 2014.
    http://www.cs.cmu.edu/~andrewgw/andrewgwthesis.pdf
[4] http://www.cs.cmu.edu/~andrewgw/pattern/.
```
