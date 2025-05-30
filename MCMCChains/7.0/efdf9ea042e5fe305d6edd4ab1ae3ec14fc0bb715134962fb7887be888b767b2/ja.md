```
replacenames(chains::Chains, dict::AbstractDict)
```

パラメータ名を置き換え、新しい `Chains` オブジェクトを作成します。このオブジェクトは同じ基盤データを共有します。

# 例

```jldoctest
julia> chn = Chains(rand(100, 2, 2), ["one", "two"]);

julia> chn2 = replacenames(chn, "one" => "A");

julia> names(chn2)
2-element Vector{Symbol}:
 :A
 :two

julia> chn3 = replacenames(chn2, Dict("A" => "one", "two" => "B"));

julia> names(chn3) 
2-element Vector{Symbol}:
 :one
 :B
```
