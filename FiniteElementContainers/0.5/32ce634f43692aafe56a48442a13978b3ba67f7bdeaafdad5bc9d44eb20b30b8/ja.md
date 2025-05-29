```julia
assemble!(
    assembler::FiniteElementContainers.DynamicAssembler,
    K_el::AbstractMatrix{<:Number},
    M_el::AbstractMatrix{<:Number},
    block_id::Int64,
    el_id::Int64
) -> AbstractMatrix{<:Number}

```

剛性行列の組み立て
