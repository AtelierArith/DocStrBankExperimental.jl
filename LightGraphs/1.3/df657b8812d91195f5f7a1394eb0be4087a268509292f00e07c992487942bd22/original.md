```
vertex_cover(g, RandomVertexCover(); seed=-1)
```

Find a set of vertices such that every edge in `g` has some vertex in the set as  atleast one of its end point.

### Implementation Notes

Performs [Approximate Minimum Vertex Cover](https://en.wikipedia.org/wiki/Vertex_cover#Approximate_evaluation) once. Returns a vector of vertices representing the vertices in the Vertex Cover.

### Performance

Runtime: O(|V|+|E|) Memory: O(|E|) Approximation Factor: 2

### Optional Arguments

  * If `seed >= 0`, a random generator is seeded with this value.
