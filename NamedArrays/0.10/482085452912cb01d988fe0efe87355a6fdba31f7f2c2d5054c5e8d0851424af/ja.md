```
NamedArray(a::AbstractArray{T,N}, names::Tuple{N,AbstractVector}, dimnames::NTuple{N,Any}))
NamedArray(a::AbstractArray{T,N}; names::Tuple{N,AbstractVector}, dimnames::NTuple{N,Any}))
```

配列 `a` から NamedArray を構築し、各次元のインデックスの名前を `names`、次元の名前を `dimnames` とします。

`dimnames` が指定されていない場合、次元は `:A, :B, ...` と名付けられ、`names` が指定されていない場合、名前は `"1", "2", "3", ...` となります。

# 例

```jldoctest
julia> NamedArray([1 2 3; 4 5 6])
2×3 Named Matrix{Int64}
A ╲ B │ 1  2  3
──────┼────────
1     │ 1  2  3
2     │ 4  5  6


julia> NamedArray([1 2 3; 4 5 6]; names=(["a", "b"], 1:3))
2×3 Named Matrix{Int64}
A ╲ B │ 1  2  3
──────┼────────
a     │ 1  2  3
b     │ 4  5  6


julia> NamedArray([1 2 3; 4 5 6]; dimnames=("rows", "cols"))
2×3 Named Matrix{Int64}
rows ╲ cols │ 1  2  3
────────────┼────────
1           │ 1  2  3
2           │ 4  5  6

julia> NamedArray([1 2; 3 4; 5 6], (["一", "二", "三"], ["first", "second"]), ("cmn", "en"))
3×2 Named Matrix{Int64}
cmn ╲ en │  first  second
─────────┼───────────────
一       │      1       2
二       │      3       4
三       │      5       6
```
