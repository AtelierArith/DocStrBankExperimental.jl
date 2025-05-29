```
MAGEMin_bulk, MAGEMin_ox; = convertBulk4MAGEMin(bulk_in::T1,bulk_in_ox::Vector{String},sys_in::String,db::String) where {T1 <: AbstractVector{Float64}}
```

receives bulk-rock composition in [mol,wt] fraction and associated oxide list and sends back bulk-rock composition converted for MAGEMin use
