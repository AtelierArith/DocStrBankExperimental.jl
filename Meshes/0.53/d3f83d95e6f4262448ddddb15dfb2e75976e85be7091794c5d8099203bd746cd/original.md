```
measurematrix(mesh)
```

The measure (or "mass") matrix of the `mesh`, i.e. a diagonal matrix with entries `Mᵢᵢ = 2Aᵢ` where `Aᵢ` is (one-third of) the sum of the areas of triangles sharing vertex `i`.

The discrete cotangent Laplace-Beltrami operator can be written as `Δ = M⁻¹L`. When solving systems of the form `Δu = f`, it is useful to write `Lu = Mf` and exploit the symmetry of `L`.
