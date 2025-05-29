```
CanonicalSymplecticMatrix{T}(n::Integer)
```

は、型 `T` のサイズ `(n, n)` の標準的なシンプレクティック行列を構築します。`n` は偶数かつ正でなければなりません。ここで定義されている標準的なシンプレクティック行列の形については、例を参照してください。

# 例

```jldoctest
julia> CanonicalSymplecticMatrix(4)
4×4 CanonicalSymplecticMatrix{Int64}:
 0  0  -1   0
 0  0   0  -1
 1  0   0   0
 0  1   0   0

julia> CanonicalSymplecticMatrix{Int32}(6)
6×6 CanonicalSymplecticMatrix{Int32}:
 0  0  0  -1   0   0
 0  0  0   0  -1   0
 0  0  0   0   0  -1
 1  0  0   0   0   0
 0  1  0   0   0   0
 0  0  1   0   0   0
```
