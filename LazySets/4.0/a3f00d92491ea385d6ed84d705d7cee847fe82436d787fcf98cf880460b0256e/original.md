```
an_element(P::AbstractPolyhedron; [solver]=default_lp_solver(eltype(P)))
```

Return some element of a polyhedron.

### Input

  * `P`       – polyhedron
  * `solver`  – (optional, default: `default_lp_solver(N)`) LP solver

### Output

An element of the polyhedron, or an error if the polyhedron is empty.

### Algorithm

An element is obtained by solving a feasibility linear program.
