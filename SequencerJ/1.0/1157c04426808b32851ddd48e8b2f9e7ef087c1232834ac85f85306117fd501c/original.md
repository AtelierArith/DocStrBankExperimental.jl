`julia`

`elongation(g, startidx)`

Returns the ratio of the graph g's half-length (mean of path distances) over the  half-width, defined as the mean count of shortest paths from the center node of a minimum spanning tree over the graph. This function calls the `dijkstra_shortest_paths`  function in `LightGraphs`.
