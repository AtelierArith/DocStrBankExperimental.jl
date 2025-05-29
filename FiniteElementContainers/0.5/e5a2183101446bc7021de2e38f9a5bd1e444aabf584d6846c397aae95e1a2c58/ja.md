```julia
assemble!(
    assembler::FiniteElementContainers.StaticAssembler,
    K_el::AbstractMatrix,
    block_id::Int64,
    el_id::Int64
) -> Any

```

剛性マトリックスのアセンブリ
