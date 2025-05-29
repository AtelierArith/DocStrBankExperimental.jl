```
IntrinsicSubspaceHomotopy(F::System, V::LinearSubspace, W::LinearSubspace)
IntrinsicSubspaceHomotopy(F::AbstractSystem, V::LinearSubspace, W::LinearSubspace)
```

Creates a homotopy $H(x,t) = F(γ(t)x)$ where $γ(t)$ is a family of affine subspaces such that $γ(1) = V$ and $γ(0) = W$. Here $γ(t)$ is the geodesic between `V` and `W` in the affine Grassmanian, i.e., it is the curve of minimal length connecting `V` and `W`. See also [`LinearSubspace`](@ref) and [`geodesic`](@ref) and the references therein.
