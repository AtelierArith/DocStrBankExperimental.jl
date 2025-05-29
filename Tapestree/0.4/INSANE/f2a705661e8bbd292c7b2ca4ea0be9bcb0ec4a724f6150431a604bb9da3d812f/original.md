```
treelength(Ξ  ::Vector{T},
           ets::Vector{Float64},
           bst::Vector{Float64},
           eix::Vector{Int64})  where {T <: iTf}
```

Return the branch length sum of `tree` at different epochs, initialized at `l`.
