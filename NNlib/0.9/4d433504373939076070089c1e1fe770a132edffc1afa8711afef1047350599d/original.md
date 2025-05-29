```
lpnormpool(x, p::Real, k::NTuple{N, Integer}; pad=0, stride=k)
```

Perform Lp pool operation with value of the Lp norm `p` and window size `k` on input tensor `x`, also known as LPPool in pytorch. This pooling operator from [Learned-Norm Pooling for Deep Feedforward and Recurrent Neural Networks](https://arxiv.org/abs/1311.1780).

Arguments:

  * `x` and `k`: Expects `ndim(x) ∈ 3:5`, and always `length(k) == ndim(x) - 2`
  * `p` is restricted to `0 < p < Inf`.
  * `pad`: See [`pad_zeros`](@ref) for details.
  * `stride`: Either a tuple with the same length as `k`, or one integer for all directions. Default is `k`.

For all elements `x` in a size `k` window, lpnormpool computes `(∑ᵢ xᵢ^p)^(1 / p)` as an element of the output.

Thus `lpnormpool(x, 1, k) ./ prod(k) ≈ meanpool(x, k)` and `lpnormpool(x, 2, k).^2 ./ prod(k) ≈ meanpool(x.^2, k)`.
