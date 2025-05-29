```
LightGraphs
```

An optimized graphs package.

Simple graphs (not multi- or hypergraphs) are represented in a memory- and time-efficient manner with adjacency lists and edge sets. Both directed and undirected graphs are supported via separate types, and conversion is available from directed to undirected.

The project goal is to mirror the functionality of robust network and graph analysis libraries such as NetworkX while being simpler to use and more efficient than existing Julian graph libraries such as Graphs.jl. It is an explicit design decision that any data not required for graph manipulation (attributes and other information, for example) is expected to be stored outside of the graph structure itself. Such data lends itself to storage in more traditional and better-optimized mechanisms.

[Full documentation](http://codecov.io/github/JuliaGraphs/LightGraphs.jl) is available, and tutorials are available at the [JuliaGraphsTutorials repository](https://github.com/JuliaGraphs/JuliaGraphsTutorials).
