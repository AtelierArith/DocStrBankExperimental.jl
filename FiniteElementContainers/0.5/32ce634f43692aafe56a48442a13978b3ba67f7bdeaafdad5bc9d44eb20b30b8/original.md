```julia
assemble!(
    assembler::FiniteElementContainers.DynamicAssembler,
    K_el::AbstractMatrix{<:Number},
    M_el::AbstractMatrix{<:Number},
    block_id::Int64,
    el_id::Int64
) -> AbstractMatrix{<:Number}

```

assembly for stiffness matrix
