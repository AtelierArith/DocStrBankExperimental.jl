```
generate_stochastic_structure(m::Model)
```

Generate the stochastic structure for given SpineOpt model.

The stochastic structure is a directed acyclic graph (DAG) where the vertices are the `stochastic_scenario` objects, and the edges are given by the `parent_stochastic_scenario__child_stochastic_scenario` relationships.

After this, you can call `active_stochastic_paths` to slice the generated structure.
