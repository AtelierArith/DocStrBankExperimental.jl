```
Lattice(data::AbstractMatrix)
```

行列から `Lattice` を構築します。

!!! note
    行列の基底ベクトルは列として保存されます。


# 例

```jldoctest
julia> Lattice([
           1.2 4.5 7.8
           2.3 5.6 8.9
           3.4 6.7 9.1
       ])
Lattice{Float64}
 1.2  4.5  7.8
 2.3  5.6  8.9
 3.4  6.7  9.1
```
