A `Partition` is a set of nonempty, pairwise disjoint sets. A new `Partition` is created by specifying the ground set `A` and calling `Partition(A)`. The set `A` may be either a `Set{T}` for some type `T` or an `BitSet`.

The parameter `A` may also be a list (one-dimensional array).

In addition, `Partition(n)` for a nonnegative integer `n` creates a partition of the set {1,2,...,n}.

The datatype `Partition` is, essentially, a wrapper around the `DataStructures.DisjointSets` type.
