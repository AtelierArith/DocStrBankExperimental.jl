```
light_cone_embedding(s, γ, τ, r0, c, bc=PeriodicBoundary()) → embedding
```

Create a [`SpatioTemporalEmbedding`](@ref) instance that includes spatial and temporal neighbors of a point based on the notion of a *light cone*.

The embedding is to be used with data from `s`.

## Description

Information does not travel instantly but with some finite speed `c ≥ 0.0`. This constructor creates a cone-like embedding including all points in space and time, whose value can influence a prediction based on the information speed `c`. `γ` is the number of temporal steps in the past to be included in the embedding, where each step in the past has additional delay time `τ::Int`. `γ=0` corresponds to using only the present. `r0` is the initial radius at the top of the cone, i.e. the radius of influence at the present. `bc` is the boundary condition.

The radius of the light cone evolves as: `r_i = i*τ*c + r0` for each step `i ∈ 0:γ`.

As an example, in a one-dimensional system with `γ = 1, τ = 2, r0 = 1`, the embedding looks like (`□` = current point (included *by definition* in the embedding), `o` point to be predicted using [`temporalprediction`](@ref), `x` = points included in the embedding, `.` = points not included in the embedding)

```
time  | c = 1.0               | c = 2.0               | c = 0.0

n + 1 | ..........o.......... | ..........o.......... | ..........o..........
n     | .........x□x......... | .........x□x......... | .........x□x.........
n - 1 | ..................... | ..................... | .....................
n - τ | .......xxxxxxx....... | .....xxxxxxxxxx...... | .........xxx.........
```

Besides this example, in the official documentation we show a function `explain_light_cone` which produces a plot of the light cone for 2 spatial dimensions (great for understanding!).
