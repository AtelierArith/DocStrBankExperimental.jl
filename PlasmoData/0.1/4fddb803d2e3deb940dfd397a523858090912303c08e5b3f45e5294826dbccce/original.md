```
DataGraph{T, T1, T2, T3, M1, M2}
```

Object for building and storing undirected graphs that contain numerical data on nodes and/or edges.

DataGraphs have the following attributes:  `g`: Graphs.SimpleGraph Object  `nodes`: Vector of node names; node names are of type `Any`  `edges`: Vector of edges; edges are tuples of integers  `node_map`: dictionary pointing node name to node number  `edge_map`: dictionary pointing tuple (node*name1, node*name2) to (node*number1, node*number2)  `node_data`: NodeData object with attributes and data  `edge_data`: EdgeData object with attributes and data  `graph_data`: GraphData object with attributes and data
