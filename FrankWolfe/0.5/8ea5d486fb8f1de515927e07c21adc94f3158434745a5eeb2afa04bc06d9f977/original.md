```
blended_conditional_gradient(f, grad!, lmo, x0)
```

Entry point for the Blended Conditional Gradient algorithm. See Braun, Gábor, et al. "Blended conditonal gradients" ICML 2019. The method works on an active set like [`FrankWolfe.away_frank_wolfe`](@ref), performing gradient descent over the convex hull of active vertices, removing vertices when their weight drops to 0 and adding new vertices by calling the linear oracle in a lazy fashion.
