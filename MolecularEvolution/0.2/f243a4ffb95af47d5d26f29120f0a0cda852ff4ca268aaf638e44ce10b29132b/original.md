Performs a BFS map-reduce over the tree, starting at a given node For each node, map*reduce is called as:    map*reduce(curr*node::FelNode, prev*node::FelNode, aggregator) where prev_node is the previous node visited on the path from the start node to the current node It is expected to update the aggregator, and not return anything.

Not exactly conventional map-reduce, as map-reduce calls may rely on state in the aggregator added by map-reduce calls on other nodes visited earlier.
