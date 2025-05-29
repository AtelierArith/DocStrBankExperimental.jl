```
flipgraph(g::TriangulatedPolygon; kwargs..)
```

Construct the **`FlipGraph`** for the `TriangulatedPolygon` `g`.

# Arguments

  * 'modular::Bool = false' : by default, the whole flip graph is constructed. If `modular` is set to `true`, then only the modular flip graph is constructed.

In a *modular flip graph*, vertices of the flip graph are classes of isomorphisms up to renaming the vertices.  Each class is then represented by one of its elements.
