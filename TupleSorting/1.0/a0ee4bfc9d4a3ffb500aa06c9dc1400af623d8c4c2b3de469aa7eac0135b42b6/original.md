Use `StaticLengthSortOblivious{n,Opt}()` to select a sorting algorithm adapted for collections of statically-known length. The algorithm is an oblivious merge sort that optionally uses the sorting networks from the `OptimalSortingNetworks` package for speeding up the base cases. The sort is not stable.

The value `n`, which must be a nonnegative integer, indicates that the hardcoded sorting networks from `OptimalSortingNetworks` should be used for sorting collections containing less than `n` elements, when supported by `OptimalSortingNetworks`. Choose a large `n`, `100`, for example, to use sorting networks for all collections supported by `OptimalSortingNetworks`.

The type `Opt` may be [`SmallDepth`](@ref) or [`SmallSize`](@ref).
