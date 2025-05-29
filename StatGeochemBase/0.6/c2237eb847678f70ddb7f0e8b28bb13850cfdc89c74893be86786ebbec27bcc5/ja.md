```julia
hashdataset(ds::Union{Dict, NamedTuple}; digits::Number=3, elements=keys(ds))
```

データセットの各行のハッシュ値を計算します。デフォルトでは、スケールに関係なく、各数値の最初の3桁の`digits`のみを考慮します。

### 例

```julia
julia> ds = (La=rand(5), Yb=rand(5)/10)
NamedTuple with 2 elements:
La  = Vector{Float64}(5,)     [0.580683620945775 ... 0.23810020661332487]
Yb  = Vector{Float64}(5,)     [0.014069255862588826 ... 0.067367584177675]

julia> hashdataset(ds)
5-element Vector{UInt64}:
0x89a02fa88348e07c
0x181e78f0ad2af144
0xa3811bd05cca4743
0xfcfe1b6edf0c81cf
0x647868efa9352972
```
