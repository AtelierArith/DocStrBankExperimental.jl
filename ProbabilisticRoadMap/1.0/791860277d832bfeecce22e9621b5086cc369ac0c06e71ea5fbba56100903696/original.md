```
add_prm_edges!(prm,src_node_num,max_num_edges,is_edge_valid,edge_cost)
```

The function adds edges for a given node in the prm (graph).

# Arguments

  * `prm::MetaGraph` -> graph to which new edges will be added
  * `src_node_num::Int` -> the node number in the prm (graph) for which new edges will be added
  * `max_num_edges::Int` -> the maximum number of edges this node can have in the prm (graph)
  * `is_edge_valid::Function` -> function that checks if a given edge is valid to be added to the graph. It takes in the prm (graph), source node state and destination node state as inputs and returns true or false   (This function can be used to check if the edge connecting the node with source node state and the node with destination node state passes through an obstacle in the environment or not).

```julia-repl
    is_edge_valid(prm,src_node_state,des_node_state)
```

  * `edge_cost::Function` -> function that computes the cost of an edge between two nodes of the graph. It takes in the prm (graph), source node state and destination node state as inputs and returns the cost of the edge connecting these nodes   (For a 2D environment where the node state is (x,y) positions, this function can return the euclidean distance between the two nodes). It will be called like this: `edge_cost(prm,src_node_state,des_node_state)`

```julia-repl
    edge_cost(prm,src_node_state,des_node_state)
```

# Example

```julia-repl
add_prm_edges!(prm, 11, 5, is_edge_valid, edge_cost)
```
