```
ttsvd(red_style::TTSVDRanks,A::AbstractArray) -> AbstractVector{<:AbstractArray}
ttsvd(red_style::TTSVDRanks,A::AbstractArray,X::AbstractRankTensor) -> AbstractVector{<:AbstractArray}
```

Tensor train SVD of `A`. When provided, `X` is a norm tensor (representing a symmetric, positive definite matrix) with respect to which the output is made orthogonal. Note: if `ndims(A)` = N, the length of the ouptput is `N-1`, since we are not interested in reducing the axis of the parameters. Check [this](https://arxiv.org/abs/2412.14460) reference for more details
