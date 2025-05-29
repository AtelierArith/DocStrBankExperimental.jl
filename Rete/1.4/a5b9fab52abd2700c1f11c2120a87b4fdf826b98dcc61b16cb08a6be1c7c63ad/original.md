AbstractMemoryNode is the abstract supertype of all Rete memory nodes.

Each concrete subtype should implement [`is_memory_for_type`](@ref) to determine if it stores that type of fact.

A memory node should remember exactly one copy of each fact it receives and return each fact it has remembered exactly once for any given call to [`askc`](@ref).

A memory node should only remember facts which match the type that the memory node is defined to store.  Not any of its subtypes.
