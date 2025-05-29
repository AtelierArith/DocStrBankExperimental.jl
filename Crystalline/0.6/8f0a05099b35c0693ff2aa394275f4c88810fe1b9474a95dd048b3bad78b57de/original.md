```julia
generate(
    gens::AbstractArray{Crystalline.SymOperation{D}, 1};
    cntr,
    modτ,
    Nmax
) -> Crystalline.GenericGroup

```

Return the group generated from a finite set of generators `gens`.

## Keyword arguments

  * `cntr` (default, `nothing`): check equivalence of operations modulo primitive lattice vectors (see also `isapprox(::SymOperation, ::SymOperation, cntr::Union{Nothing, Char})`;  only nonequivalent operations are included in the returned group.
  * `modτ` (default, `true`): the group composition operation can either be taken modulo lattice vectors (`true`) or not (`false`, useful e.g. for site symmetry groups). In this case, the provided generators will also be taken modulo integer lattice translations.
  * `Nmax` (default, `256`): the maximum size of the generated group. This is essentially a cutoff set to ensure halting of execution in case the provided set of generators do not define a *finite* group (especially relevant if `modτ=false`). If more operations than `Nmax` are generated, the method throws an overflow error.
