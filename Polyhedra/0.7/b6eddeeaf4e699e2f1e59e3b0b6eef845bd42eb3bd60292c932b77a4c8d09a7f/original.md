```
translate(p::Polyhedra.Rep, v::AbstractVector)
```

Computes translation of the polyhedron `p` with the vector `v`. That is, computes

$$
\{\, x + v \mid x \in p \,\}.
$$

By default, if the H-representation, it simply translates every hyperplanes and halfspace, otherwise, it translates every points of the V-representation. That is, this operation can be achieved both in the H-representation and V-representation hence does not trigger any representation conversion.
