A `SimpleACSet` is an abstract type for any acset that has a certain layout

Specifically, subtypes of `SimpleACSet` are expected to have a `parts` field which is a mapping from symbols to ints, and a `subparts` field which is a mapping from symbols to columns, which are any data structure that satisfies the interface given in Columns.jl.
