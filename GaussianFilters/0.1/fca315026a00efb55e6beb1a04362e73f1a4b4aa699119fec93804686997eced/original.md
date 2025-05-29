```
belief_ellipse(b::GaussianBelief, P::Float=0.95; δ::Number=5)
```

Construct and return the x and y points of a 2D gaussian belief, with P being the total probability captured by the ellipse (P ∈ (0,1)), and δ the degree increment between points.
