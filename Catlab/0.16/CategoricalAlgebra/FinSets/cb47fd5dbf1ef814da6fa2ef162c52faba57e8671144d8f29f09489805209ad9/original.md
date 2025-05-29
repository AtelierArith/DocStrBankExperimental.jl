Algorithm for limit of cospan or multicospan with feet being finite sets.

In the context of relational databases, such limits are called *joins*. The trivial join algorithm is [`NestedLoopJoin`](@ref), which is algorithmically equivalent to the generic algorithm `ComposeProductEqualizer`. The algorithms [`HashJoin`](@ref) and [`SortMergeJoin`](@ref) are usually much faster. If you are unsure what algorithm to pick, use [`SmartJoin`](@ref).
