```
struct DynamicSelection <: HierarchicalSelection .. end
```

A hierarchical, mutable, selection with arbitrary addresses.

Can be mutated with the following methods:

```
Base.push!(selection::DynamicSelection, addr)
```

Add the address and all of its sub-addresses to the selection.

Example:

```julia
selection = select()
@assert !(:x in selection)
push!(selection, :x)
@assert :x in selection
```

```
set_subselection!(selection::DynamicSelection, addr, other::Selection)
```

Change the selection status of the given address and its sub-addresses that defined by `other`.

Example:

```julia
selection = select(:x)
@assert :x in selection
subselection = select(:y)
set_subselection!(selection, :x, subselection)
@assert (:x => :y) in selection
@assert !(:x in selection)
```

Note that `set_subselection!` does not copy data in `other`, so `other` may be mutated by a later calls to `set_subselection!` for addresses under `addr`.
