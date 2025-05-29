```
sort_bibliography!(
    bibliography::DataStructures.OrderedDict{String,Entry},
    sorting_rule::Symbol = :key
    )
```

Sorts the bibliography in place.

The sorting order can be set by specifying the `sorting_rule`. The sorting is implemented via `isless()` functions. For detailed insight have a look at the `isless()` implementation of Julia and `BibInternal.jl`.

Supported symbols for `sorting_rule` are:

  * `:key` **(default)**: sort by bibliography keys e.g. BibTeX keys or `:id`
  * the sorting rules defined in [`sorting_rules`](@ref)

!!! info "Note:"
    The sorting is not following explicitly bibliographic alphabetizing conventions. It follows standard comparator behaviour implied by the implemented `isless()` functions (string comparators).

