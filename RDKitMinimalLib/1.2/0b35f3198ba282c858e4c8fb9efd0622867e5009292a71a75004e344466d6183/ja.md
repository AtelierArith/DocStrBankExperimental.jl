```
get_morgan_fp(mol::Mol, details::Union{Dict{String,Any},Nothing}=nothing)::String
```

モルガン（ECFPのような）フィンガープリントを取得します。

```julia
mfp = get_morgan_fp(mol)
```

```julia
fp_details = Dict{String, Any}("nBits" => 512, "radius" => 2)
morgan_fp = get_morgan_fp(mol, fp_details)

```
