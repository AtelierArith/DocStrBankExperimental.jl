```
Aspad = paddedviews(fillvalue, A1, A2, ...; [dims])
```

配列 `A1`, `A2`, ... を共通のサイズまたは軸のセットにパディングします。これは、すべての入力配列を囲む軸の範囲として選択されます。

パディングは、次元 `dims` の一方向に適用されます。たとえば、2次元の場合、新しい配列の右下部分に値が埋められます。*両方*の方向にパディングが必要な場合は、[`sym_paddedviews`](@ref) を使用してください。

元の配列 `A` の軸は、パディングされた結果 `Ap` に保持されるため、`Ap[CartesianIndices(A)] == A` であることが真です。

# 例:

```jldoctest
julia> using PaddedViews

julia> a1 = reshape([1, 2, 3], 3, 1)
3×1 Matrix{Int64}:
 1
 2
 3

julia> a2 = [4 5 6]
1×3 Matrix{Int64}:
 4  5  6

julia> a1p, a2p = paddedviews(-1, a1, a2);

julia> a1p
3×3 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(3), Base.OneTo(3))) with eltype Int64:
 1  -1  -1
 2  -1  -1
 3  -1  -1

julia> a2p
3×3 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(3), Base.OneTo(3))) with eltype Int64:
  4   5   6
 -1  -1  -1
 -1  -1  -1

julia> a1p[CartesianIndices(a1)]
3×1 Matrix{Int64}:
 1
 2
 3
```

`dims` キーワードは、指定された次元に対してのみパディングを許可します。

```jldoctest; setup=:(using PaddedViews)
julia> a1 = reshape(collect(1:9), 3, 3)
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> a2 = [4 5;6 7]
2×2 Matrix{Int64}:
 4  5
 6  7

julia> a1f, a2f = paddedviews(-1, a1, a2; dims=1);

julia> a2f
3×2 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(3), Base.OneTo(2))) with eltype Int64:
  4   5
  6   7
 -1  -1

julia> a1f, a2f = paddedviews(-1, a1, a2; dims=(1,2));

julia> a2f
3×3 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(3), Base.OneTo(3))) with eltype Int64:
  4   5  -1
  6   7  -1
 -1  -1  -1
```
