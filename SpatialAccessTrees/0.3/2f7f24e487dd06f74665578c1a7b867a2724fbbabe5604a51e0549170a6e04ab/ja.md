```
struct Sat{DT<:SemiMetric,DBT<:AbstractDatabase} <: AbstractSearchIndex
    dist::DT
    db::DBT
    root::UInt32
    # parents::Vector{UInt32}
    children::Vector{Union{Nothing,Vector{UInt32}}}
    cov::Vector{Float32} # leafs: ``- d(parent, leaf)``, internal: ``\max \{d(parent, u) | u \in children(parent)\}``
end
```

空間アクセスツリーデータ構造。高レベルのコンストラクタについては`Sat`関数を参照してください。
