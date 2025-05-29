```
to_independent_set!(config::AbstractVector, graph::AbstractGraph)
```

Eliminate vertices in `config` so that remaining vertices do not have connected edges. This algorithm is a naive vertex elimination that does not nesesarily give the maximum possible vertex set.

```@example
# run the following code in Atom/VSCode
atoms = [(0.0, 1.0), (1.0, 0.), (2.0, 0.0), (1.0, 1.0), (1.0, 2.0), (2.0, 2.0)]
graph = unit_disk_graph(atoms, 1.5)

config = [1, 1, 1, 0, 1, 1]
viz_config(atoms, graph, config)

to_independent_set!(config, graph)
viz_config(atoms, graph, config)
```
