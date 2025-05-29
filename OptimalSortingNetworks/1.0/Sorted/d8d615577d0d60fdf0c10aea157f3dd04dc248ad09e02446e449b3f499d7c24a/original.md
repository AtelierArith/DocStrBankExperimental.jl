Calling `sorted(minmax, coll, objective)` yields `coll` sorted according to the `minmax` compare/exchange element, which must be callable like so: `minmax(l, r)`, where `l` and `r` are elements of `coll`. `objective` must be either `Depth()` or `Size()`, see [`Depth`](@ref) and [`Size`](@ref).

The `minmax` and `objective` arguments are optional. Configure defaults for `minmax` by overloading [`default_minmax_by`](@ref) and/or [`default_minmax_less`](@ref). The objective `objective` currently defaults to `Size()`.

The size vs depth choice only affects the structure of the sorting network, it will not affect the correctness of the sort (assuming the selected compare/exchange element is correct). It's unclear what use there is for the `Depth()` choice, so just stay with the default unless you know you need a network with minimal depth.

Not a stable sort.

The collection `coll` must be either:

1. A `Tuple` of no more than eleven elements, currently.
2. An `AbstractVector` of no more than five elements, currently. The upper bound is smaller than the one for tuples to minimize the precompilation cost. The return type is `Vector`.
