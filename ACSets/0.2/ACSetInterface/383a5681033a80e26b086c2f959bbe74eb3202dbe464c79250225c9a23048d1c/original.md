Remove part from a C-set.

The part is removed using the "pop and swap" strategy familiar from [Graphs.jl](https://github.com/JuliaGraphs/Graphs.jl), where the "removed" part is actually replaced by the last part, which is then deleted. This strategy has important performance benefits since only the last part must be assigned a new ID, as opposed to assigning new IDs to *every* part following the removed part.

The removal operation is *not* recursive. When a part is deleted, any superparts incident to it are retained, but their subparts become undefined (equal to the integer zero). For example, in a graph, if you call `rem_part!` on a vertex, the edges incident the `src` and/or `tgt` vertices of the edge become undefined but the edge itself is not deleted.

Indexing has both positive and negative impacts on performance. On the one hand, indexing reduces the cost of finding affected superparts from linear time to constant time. On the other hand, the indices of subparts must be updated when the part is removed. For example, in a graph, indexing `src` and `tgt` makes removing vertices faster but removing edges (slightly) slower.

See also: [`rem_parts!`](@ref).
