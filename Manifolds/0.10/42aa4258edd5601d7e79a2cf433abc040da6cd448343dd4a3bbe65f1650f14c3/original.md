```
injectivity_radius(G::SpecialOrthogonal)
injectivity_radius(G::Orthogonal)
injectivity_radius(M::Rotations)
injectivity_radius(M::Rotations, ::ExponentialRetraction)
```

Return the radius of injectivity on the [`Rotations`](@ref) manifold `M`, which is $π\sqrt{2}$. [^1]

[^1]: > For a derivation of the injectivity radius, see [sethaxen.com/blog/2023/02/the-injectivity-radii-of-the-unitary-groups/](https://sethaxen.com/blog/2023/02/the-injectivity-radii-of-the-unitary-groups/).
