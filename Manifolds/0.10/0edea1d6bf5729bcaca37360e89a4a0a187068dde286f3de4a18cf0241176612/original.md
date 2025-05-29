```
change_representer(M::ProbabilitySimplex, ::EuclideanMetric, p, X)
```

Given a tangent vector with respect to the metric from the embedding, the [`EuclideanMetric`](@extref `ManifoldsBase.EuclideanMetric`), the representer of a linear functional on the tangent space is adapted as $Z = p .* X .- p .* dot(p, X)$. The first part “compensates” for the division by $p$ in the Riemannian metric on the [`ProbabilitySimplex`](@ref) and the second part performs appropriate projection to keep the vector tangent.

For details see Proposition 2.3 in [AastroemPetraSchmitzerSchnoerr:2017](@cite).
