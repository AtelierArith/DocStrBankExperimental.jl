```
tree_mapreduce(
    f::Function,
    [f_branch::Function,]
    op::Function,
    tree::AbstractNode,
    [result_type::Type=Undefined];
    f_on_shared::Function=(result, is_shared) -> result,
    break_sharing::Val=Val(false),
)
```

Map a function over a tree and aggregate the result using an operator `op`. `op` should be defined with inputs `(parent, child...) ->` so that it can aggregate both unary and binary operators. `op` will not be called for leafs of the tree. This differs from a normal `mapreduce` in that it allows different treatment for parent nodes than children nodes. If this is not necessary, you may use the regular `mapreduce` instead. The argument `break_sharing` can be used to break connections in a [`GraphNode`](@ref).

You can also provide separate functions for leaf (variable/constant) nodes and branch (operator) nodes.

# Examples

```jldoctest
julia> operators = OperatorEnum(; binary_operators=[+, *]);

julia> tree = Node(; feature=1) + Node(; feature=2) * 3.2;

julia> tree_mapreduce(t -> 1, +, tree)  # count nodes. (regular mapreduce also works)
5

julia> tree_mapreduce(t -> 1, (p, c...) -> p + max(c...), tree)  # compute depth. regular mapreduce would fail!
5

julia> tree_mapreduce(vcat, tree) do t
    t.degree == 2 ? [t.op] : UInt8[]
end  # Get list of binary operators used. (regular mapreduce also works)
2-element Vector{UInt8}:
 1
 2

julia> tree_mapreduce(vcat, tree) do t
    (t.degree == 0 && t.constant) ? [t.val] : Float64[]
end  # Get list of constants. (regular mapreduce also works)
1-element Vector{Float64}:
 3.2
```
