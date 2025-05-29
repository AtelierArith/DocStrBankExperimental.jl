```
add_prm_node!(prm,get_node_state,is_node_valid,rng,time_limit)
```

The function tries to add a new node to the given prm (graph) within the specified time limit.

# Arguments

  * `prm::MetaGraph` -> graph to which a new node (vertex) will be added
  * `get_node_state::Function` -> function that returns the state to be stored at that node. It takes in a random number generator as an input and returns the node state   (For a 2D environment, the node state could be a tuple of x and y positions).

```julia-repl
        node_state = get_node_state(rng)
```

  * `is_node_valid::Function` -> function that checks if a given node is valid to be added to the PRM. It takes in the prm (graph) and node state as inputs and returns true or false   (This function can be used to check if the node state is in free space or not).

```julia-repl
        is_node_valid(prm,node_state)
```

  * `rng::AbstractRNG` -> a random number generator object. It will be used as an input to the `get_node_state` function to generate the state for a new node in the PRM.
  * `time_limit::Real=0.2` -> specifies the time limit for adding a new node to the prm (graph)

# Output

  * `true` if a new node has been successfully added to the prm (graph), else `false`

# Example

```julia-repl
add_prm_node!(prm,get_node_state,is_node_valid,MersenneTwister(11),1.0)
```
