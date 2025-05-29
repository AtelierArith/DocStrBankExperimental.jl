```
subset(varinfo::AbstractVarInfo, vns::AbstractVector{<:VarName})
```

`varinfo`を`vns`の変数のみを含むように部分集合を作成します。

返される値の変数の順序は`varinfo`と同じになります。

# 例

```jldoctest varinfo-subset; setup = :(using Distributions, DynamicPPL)
julia> @model function demo()
           s ~ InverseGamma(2, 3)
           m ~ Normal(0, sqrt(s))
           x = Vector{Float64}(undef, 2)
           x[1] ~ Normal(m, sqrt(s))
           x[2] ~ Normal(m, sqrt(s))
       end
demo (generic function with 2 methods)

julia> model = demo();

julia> varinfo = VarInfo(model);

julia> keys(varinfo)
4-element Vector{VarName}:
 s
 m
 x[1]
 x[2]

julia> for (i, vn) in enumerate(keys(varinfo))
           varinfo[vn] = i
       end

julia> varinfo[[@varname(s), @varname(m), @varname(x[1]), @varname(x[2])]]
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0

julia> # `m`のみを抽出します。
       varinfo_subset1 = subset(varinfo, [@varname(m),]);


julia> keys(varinfo_subset1)
1-element Vector{VarName{:m, typeof(identity)}}:
 m

julia> varinfo_subset1[@varname(m)]
2.0

julia> # `s`と`x[2]`の両方を抽出します。
       varinfo_subset2 = subset(varinfo, [@varname(s), @varname(x[2])]);

julia> keys(varinfo_subset2)
2-element Vector{VarName}:
 s
 x[2]

julia> varinfo_subset2[[@varname(s), @varname(x[2])]]
2-element Vector{Float64}:
 1.0
 4.0
```

`subset`は特に[`merge(varinfo::AbstractVarInfo)`](@ref)と組み合わせると便利です。

```jldoctest varinfo-subset
julia> # 2つをマージします。
       varinfo_subset_merged = merge(varinfo_subset1, varinfo_subset2);

julia> keys(varinfo_subset_merged)
3-element Vector{VarName}:
 m
 s
 x[2]

julia> varinfo_subset_merged[[@varname(s), @varname(m), @varname(x[2])]]
3-element Vector{Float64}:
 1.0
 2.0
 4.0

julia> # 元のものと2つをマージします。
       varinfo_merged = merge(varinfo, varinfo_subset_merged);

julia> keys(varinfo_merged)
4-element Vector{VarName}:
 s
 m
 x[1]
 x[2]

julia> varinfo_merged[[@varname(s), @varname(m), @varname(x[1]), @varname(x[2])]]
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
```

# 注意

## 型の安定性

!!! warning
    この関数は、`vns`が同じシンボルの変数名のみを含む場合にのみ型が安定します。例えば、`[@varname(m[1]), @varname(m[2])]`は型が安定しますが、`[@varname(m[1]), @varname(x)]`は型が安定しません。

