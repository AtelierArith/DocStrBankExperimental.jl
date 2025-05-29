```
MAGEMin_bulk, MAGEMin_ox; = convertBulk4MAGEMin(bulk_in::T1,bulk_in_ox::Vector{String},sys_in::String,db::String) where {T1 <: AbstractVector{Float64}}
```

は、[mol,wt] フラクションのバルク岩組成と関連する酸化物リストを受け取り、MAGEMin 用に変換されたバルク岩組成を返します。
