```
CountingTropical{T,CT} <: Number
```

カウントトロピカル数型は、半環代数でもあります。これは、カウント用の追加フィールドを持つトロピカル代数であり、[arXiv:2008.06888](https://arxiv.org/abs/2008.06888)で紹介されています。

## 例

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
