```julia
getspin(tm::AbstractTBModel, α::Int64, k::AbstractVector{<:Real})
```

Calculate ⟨n|σα|m⟩ at `k` point.

If `tm` is a TBModel, the function checks whether `tm.isspinful` is true.
