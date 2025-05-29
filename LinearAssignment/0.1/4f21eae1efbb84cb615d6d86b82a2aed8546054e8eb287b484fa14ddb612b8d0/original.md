```
compute_cost(L::LAWorkspaceCSC, C::SparseMatrixCSC{Tv}) -> Tv

compute_cost(
    L::LAWorkspaceCSC,
    m::Integer,
    n::Integer,
    colptr::AbstractVector{<:Integer},
    rowval::AbstractVector{<:Integer},
    nzval::AbstractVector{Tv},
) -> Tv

compute_cost(
    m::Integer,
    n::Integer,
    colptr::AbstractVector{<:Integer},
    rowval::AbstractVector{<:Integer},
    nzval::AbstractVector{Tv},
    I::AbstractVector{<:Integer}
) -> Tv
```

Return the cost of the assignment.
