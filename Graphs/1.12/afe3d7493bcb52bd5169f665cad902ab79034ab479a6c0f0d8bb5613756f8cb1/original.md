```
Graphs
```

An optimized graphs package.

Simple graphs (not multi- or hypergraphs) are represented in a memory- and time-efficient manner with adjacency lists and edge sets. Both directed and undirected graphs are supported via separate types, and conversion is available from directed to undirected.

The project goal is to mirror the functionality of robust network and graph analysis libraries such as NetworkX while being simple to use and efficient. It is an explicit design decision that any data not required for graph manipulation (attributes and other information, for example) is expected to be stored outside of the graph structure itself. Such data lends itself to storage in more traditional and better-optimized mechanisms.

[Full documentation](https://juliagraphs.org/Graphs.jl/stable/) is available, and tutorials are available at the [JuliaGraphsTutorials repository](https://github.com/JuliaGraphs/JuliaGraphsTutorials).
