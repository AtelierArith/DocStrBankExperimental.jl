```julia
setposition!(
    tm::TBModel,
    R::AbstractVector{<:Integer},
    n::Int64,
    m::Int64,
    α::Int64,
    pos::Number;
    position_tolerance::Real=1.0e-4
)
```

Set ⟨0n|$r_α$|Rm⟩ to `pos` for `tm`. Overlap matrices must be set before this method is called if `tm` is not orthogonal.

`position_tolerance` is used to check wehther the value is compatible with `tm.site_positions` (if not missing).
