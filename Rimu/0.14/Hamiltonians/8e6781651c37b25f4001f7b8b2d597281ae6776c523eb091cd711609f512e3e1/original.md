```
get_all_blocks(h::Union{HOCartesianContactInteractions,HOCartesianEnergyConservedPerDim};
    target_energy = nothing,
    max_energy = nothing,
    max_blocks = nothing,
    method = :vertices,
    kwargs...) -> df
```

Find all distinct blocks of `h`. Returns a `DataFrame` with columns

  * `block_id`: index of block in order found
  * `block_E0`: noninteracting energy of all elements in the block
  * `block_size`: number of elements in the block
  * `addr`: first address that generates the block with e.g. [`BasisSetRepresentation`](@ref)
  * `indices`: tuple of mode indices that allow recreation of the generating address   `addr`; in this case use e.g. `BoseFS(M; indices .=> 1)` This is useful when   the `DataFrame` is loaded from file since `Arrow.jl` converts custom   types to `NamedTuple`s.
  * `t_basis`: time to generate the basis for each block

Keyword arguments:

  * `target_energy`: only blocks with this noninteracting energy are found
  * `max_energy`: only blocks with noninteracting energy less than this are found
  * `max_blocks`: exit after finding this many blocks
  * `method`: Choose between `:vertices` and `:comb` for method of enumerating   tuples of quantum numbers
  * `save_to_file=nothing`: if set then the `DataFrame` recording blocks is saved   after each new block is found
  * additional `kwargs`: passed to `isapprox` for comparing block energies.   Useful for anisotropic traps

Note: If `h` was constructed with option `block_by_level = false` then the block seeds `addr` are determined by parity. In this case the blocks are not generated; `t_basis` will be zero, and `block_size` will be an estimate. Pass the seed addresses to [`BasisSetRepresentation`](@ref) with an appropriate `filter` to generate the blocks.
