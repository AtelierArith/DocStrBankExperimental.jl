```
Lattice(𝐡::AbstractVector, 𝐢::AbstractVector, 𝐣::AbstractVector)
```

三つの基底ベクトルから `Lattice` を構築します。

# 例

```jldoctest
julia> 𝐡, 𝐢, 𝐣 = [1.2, 2.3, 3.4], [4.5, 5.6, 6.7], [7.8, 8.9, 9.10];

julia> Lattice(𝐡, 𝐢, 𝐣)
Lattice{Float64}
 1.2  4.5  7.8
 2.3  5.6  8.9
 3.4  6.7  9.1
```
