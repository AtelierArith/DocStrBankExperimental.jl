```
laplacematrix(mesh; kind=nothing)
```

The Laplace-Beltrami (a.k.a. Laplacian) matrix of the `mesh`. Optionally, specify the `kind` of discretization.

## Available discretizations

  * `:uniform`   - `Lᵢⱼ = 1 / |𝒜(i)|, ∀j ∈ 𝒜(i)`
  * `:cotangent` - `Lᵢⱼ = cot(αᵢⱼ) + cot(βᵢⱼ), ∀j ∈ 𝒜(i)`

where `𝒜(i)` is the adjacency relation at vertex `i`.

## References

  * Botsch et al. 2010. [Polygon Mesh Processing](http://www.pmp-book.org).
  * Pinkall, U. & Polthier, K. 1993. [Computing discrete minimal surfaces and their conjugates](https://projecteuclid.org/journals/experimental-mathematics/volume-2/issue-1/Computing-discrete-minimal-surfaces-and-their-conjugates/em/1062620735.full).
