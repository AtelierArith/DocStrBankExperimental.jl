```
iid_copies(ρBs::AbstractVector{<:AbstractMatrix}, n::Integer) -> Vector{Matrix}
```

Create a vector of all states of the form $ρ_1 \otimes \dotsm \otimes ρ_n$ where the $ρ_i$ range over the set `ρBs`.
