```
PVector{T, N} <: AbstractProjectiveVector{T, N}
```

`PVector`は、`N`個の射影空間の積$P(T)^{dᵢ}$に存在する射影ベクトル`z`を表します。基盤となるデータ構造は`Vector{T}`です。

```
PVector(v::AbstractVector, dims::NTuple{N,Int}) where N
```

射影次元`dims`を持つ射影空間の積に存在する射影ベクトル`v`を作成します。

```
PVector(v, w, ...)
```

射影ベクトルの積を作成します。

## 例

```julia
julia> PVector([1,2,3], [4, 5])
[1 : 2 : 3] × [4 : 5]

julia> PVector([1, 2, 3, 4, 5], (2, 1))
[1 : 2 : 3] × [4 : 5]

julia> PVector([1,2,3], [4, 5], [6, 7, 8])
[1 : 2 : 3] × [4 : 5] × [6 : 7 : 8]
```
