```
uniform_bell_sampler(n, d, object=:magicSimplex, precision=10)
```

Create array of `n` uniformly distributed $d^2$ Bell diagonal states represented as `CoordState` rounded to `precision` digits. 

Use `object=:enclosurePolytope` to create CoordStates in the enclosure polytope, having all $coords \leq 1/d$.
