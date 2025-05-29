```
RowProjectionVector{T} <: AbstractArray{T, 1}
```

与えられたベクトルの行のシーケンスを要素の型 `T` を持つ暗黙のベクトルとして投影します。

# コンストラクタ

```
RowProjectionVector(base, rows)
RowProjectionVector(base, rows...)
RowProjectionVector{T}(base, rows)
```

与えられた `base` ベクトルとそれに対応する `rows` のリストまたはシーケンスから新しい行投影ベクトルを作成します。行は複数回、任意の順序で使用できます。

# 例

```jldoctest; setup = :(using ImplicitArrays)
julia> v = [10, 20, 30, 40, 50];

julia> RowProjectionVector(v, [1, 3, 5])
3-element RowProjectionVector{Int64, Vector{Int64}}:
 10
 30
 50

julia> RowProjectionVector(v, 2, 3, 2)
3-element RowProjectionVector{Int64, Vector{Int64}}:
 20
 30
 20
```

!!! 注     `RowProjectionVector` を通じて要素を変更すると、実際には基になる配列の要素が変更されます。変更は `RowProjectionVector` にも反映されます。したがって、投影に複数回含まれる行の要素を変更する際には、望ましくない副作用を避けるために注意が必要です。
