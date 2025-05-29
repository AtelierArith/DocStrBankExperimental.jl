```
Chains(c::Chains, section::Union{Symbol,AbstractString})
Chains(c::Chains, sections)

特定の `section` または複数の `sections` を抽出して新しいチェーンを返します。

# 例

```

jldoctest julia> chn = Chains(rand(100, 2, 1), [:a, :b], Dict(:internals => [:a]));

julia> names(chn) 2-element Vector{Symbol}:  :a  :b

julia> chn2 = Chains(chn, :internals);

julia> names(chn2) 1-element Vector{Symbol}:  :a ```
