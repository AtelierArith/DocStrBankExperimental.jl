centroid_polygon(vertices::Vector{<:Point2D})

Uses the following formulas:

  * Cx = (1/6A)Σ(xᵢ + xᵢ₊₁)(xᵢyᵢ₊₁ - yᵢxᵢ₊₁)
  * Cy = (1/6A)Σ(yᵢ + yᵢ₊₁)(xᵢyᵢ₊₁ - yᵢxᵢ₊₁)
