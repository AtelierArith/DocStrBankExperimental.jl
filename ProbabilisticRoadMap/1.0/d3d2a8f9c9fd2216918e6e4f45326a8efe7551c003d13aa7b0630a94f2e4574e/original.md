```
generate_prm(num_nodes,max_edges,get_node_values,is_node_valid,is_edge_valid,edge_cost,rng,time_limit=0.2)
```

The function generates and returns a prm (graph) with the given number of nodes and connects them to other nodes in the prm

# Arguments

  * `num_nodes::Int` -> number of nodes to be added in the prm (graph)
  * `max_edges::Int` -> maximum number of edges each node can have in the prm (graph)
  * `get_node_state::Function` -> function that returns the state to be stored at that node. It takes in a random number generator as an input and returns the node state   (For a 2D environment, the node state could be a tuple of x and y positions).

```julia-repl
    node_state = get_node_state(rng)
```

  * `is_node_valid::Function` -> function that checks if a given node is valid to be added to the PRM. It takes in the prm (graph) and node state as inputs and returns true or false   (This function can be used to check if the node state is in free space or not).

```julia-repl
    is_node_valid(prm,node_state)

```

  * `is_edge_valid::Function` -> function that checks if a given edge is valid to be added to the graph. It takes in the prm (graph), source node state and destination node state as inputs and returns true or false   (This function can be used to check if the edge connecting the node with source node state and the node with destination node state passes through an obstacle in the environment or not).

```julia-repl
    is_edge_valid(prm,src_node_state,des_node_state)
```

  * `edge_cost::Function` -> function that computes the cost of an edge between two nodes of the graph. It takes in the prm (graph), source node state and destination node state as inputs and returns the cost of the edge connecting these nodes   (For a 2D environment where the node state is (x,y) positions, this function can return the euclidean distance between the two nodes.

```julia-repl
    edge_cost(prm,src_node_state,des_node_state)
```

  * `rng::AbstractRNG` -> a random number generator object. It will be used as an input to the `get_node_state` function to generate the state for a new node in the PRM.
  * `time_limit::Real=0.2` -> specifies the time limit for adding a new node to the prm (graph)

# Output

  * a meta graph with `num_nodes` number of vertices (nodes) where ever vertex is connected to `max_edges` or fewer other vertices

    ```
      (meta graph because every node has an attribute called `:values` which has the node values in it)
    ```

# Example

```julia-repl
generate_prm(100,5,get_node_values,is_node_valid,is_edge_valid,edge_cost,MersenneTwister(11),1.0)
```
