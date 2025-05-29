```
exactposterior(nrange::AbstractVector{<:Integer}, τCrange::AbstractVector{<:Real}, τArange::AbstractVector{<:Real}, ϵrange::AbstractVector{<:Real}, coverages::AbstractVector{<:Integer}, uniquecoverages::AbstractVector{<:Integer}, derivedreads::AbstractVector{<:Integer}, frequencies::AbstractVector{<:Real}, counts::AbstractVector{<:Integer}, messages::Integer)
```

Calculate the exact posterior up to a fixed unknown constant that depends on the data but does not depend on the parameters. 
