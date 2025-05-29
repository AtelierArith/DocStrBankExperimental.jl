```
RowProjectionMatrix{T} <: AbstractArray{T, 2}
```

与えられた行列の行のシーケンスを要素の型 `T` で暗黙的に投影する行列。

# コンストラクタ

```
RowProjectionMatrix(base, rows)
RowProjectionMatrix(base, rows...)
RowProjectionMatrix{T}(base, rows)
```

与えられた `base` 行列とそれに対応する `rows` のリストまたはシーケンスから新しい行投影行列を作成します。行は複数回、任意の順序で使用できます。

# 例

```jldoctest; setup = :(using ImplicitArrays)
julia> M = [10 20 30; 40 50 60; 70 80 90];

julia> RowProjectionMatrix(M, [1, 3])
2×3 RowProjectionMatrix{Int64, Matrix{Int64}}:
 10  20  30
 70  80  90

julia> RowProjectionMatrix(M, 2, 3, 2)
3×3 RowProjectionMatrix{Int64, Matrix{Int64}}:
 40  50  60
 70  80  90
 40  50  60
```

!!! note
    `RowProjectionMatrix` を通じて要素を変更すると、実際には基になる配列の要素が変更されます。変更は `RowProjectionMatrix` にも反映されます。したがって、投影に複数回含まれる行の要素を変更する際には、望ましくない副作用を避けるために注意が必要です。

