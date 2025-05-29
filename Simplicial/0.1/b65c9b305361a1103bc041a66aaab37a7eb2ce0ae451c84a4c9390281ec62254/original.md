```
polar_complex(C)
```

Constructs the polar complex $Γ(C)$ for the given code.

!!! Implementation notes     Vertex set is `V = union(vertices(C), map(-,vertices(C)))`. This can have strange     results if the vertex type of `C` is unsigned and the size of the vertex set is large.
