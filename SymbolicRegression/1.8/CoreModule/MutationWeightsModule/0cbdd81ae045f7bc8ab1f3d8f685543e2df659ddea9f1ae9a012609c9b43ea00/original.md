```
MutationWeights(;kws...) <: AbstractMutationWeights
```

This defines how often different mutations occur. These weightings will be normalized to sum to 1.0 after initialization.

# Arguments

  * `mutate_constant::Float64`: How often to mutate a constant.
  * `mutate_operator::Float64`: How often to mutate an operator.
  * `swap_operands::Float64`: How often to swap the operands of a binary operator.
  * `rotate_tree::Float64`: How often to perform a tree rotation at a random node.
  * `add_node::Float64`: How often to append a node to the tree.
  * `insert_node::Float64`: How often to insert a node into the tree.
  * `delete_node::Float64`: How often to delete a node from the tree.
  * `simplify::Float64`: How often to simplify the tree.
  * `randomize::Float64`: How often to create a random tree.
  * `do_nothing::Float64`: How often to do nothing.
  * `optimize::Float64`: How often to optimize the constants in the tree, as a mutation.   Note that this is different from `optimizer_probability`, which is   performed at the end of an iteration for all individuals.
  * `form_connection::Float64`: **Only used for `GraphNode`, not regular `Node`**.   Otherwise, this will automatically be set to 0.0. How often to form a   connection between two nodes.
  * `break_connection::Float64`: **Only used for `GraphNode`, not regular `Node`**.   Otherwise, this will automatically be set to 0.0. How often to break a   connection between two nodes.

# See Also

  * [`AbstractMutationWeights`](@ref SymbolicRegression.CoreModule.MutationWeightsModule.AbstractMutationWeights): Use to define custom mutation weight types.
