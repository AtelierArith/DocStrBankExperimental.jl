```
injectivity_radius(G::SpecialOrthogonal)
injectivity_radius(G::Orthogonal)
injectivity_radius(M::Rotations)
injectivity_radius(M::Rotations, ::ExponentialRetraction)
```

[`Rotations`](@ref) 多様体 `M` の注入半径を返します。これは $π\sqrt{2}$ です。 [^1]

[^1]: > 注入半径の導出については、[sethaxen.com/blog/2023/02/the-injectivity-radii-of-the-unitary-groups/](https://sethaxen.com/blog/2023/02/the-injectivity-radii-of-the-unitary-groups/) を参照してください。
