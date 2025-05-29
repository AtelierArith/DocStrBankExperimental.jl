```
CountingTropical{T,CT} <: Number
```

Counting tropical number type is also a semiring algebra. It is tropical algebra with one extra field for counting, it is introduced in [arXiv:2008.06888](https://arxiv.org/abs/2008.06888).

## Example

```jldoctest; setup=:(using TropicalNumbers)
julia> CountingTropical(1.0, 5.0) + CountingTropical(3.0, 2.0)
(3.0, 2.0)ₜ

julia> CountingTropical(1.0, 5.0) * CountingTropical(3.0, 2.0)
(4.0, 10.0)ₜ

julia> one(CountingTropicalF64)
(0.0, 1.0)ₜ

julia> zero(CountingTropicalF64)
(-Inf, 0.0)ₜ
```
