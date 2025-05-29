```
Line{N, VN<:AbstractVector{N}} <: AbstractPolyhedron{N}
```

Type that represents a line of the form

$$
    \{y ∈ ℝ^n: y = p + λd, λ ∈ ℝ\}
$$

where $p$ is a point on the line and $d$ is its direction vector (not necessarily normalized).

### Fields

  * `p` – point on the line
  * `d` – direction

### Examples

There are three constructors. The optional keyword argument `normalize` (default: `false`) can be used to normalize the direction of the resulting line to have norm 1 (w.r.t. the Euclidean norm).

1. The default constructor takes the fields `p` and `d`:

The line passing through the point $[-1, 2, 3]$ and parallel to the vector $[3, 0, -1]$:

```jldoctest
julia> Line([-1.0, 2, 3], [3.0, 0, -1])
Line{Float64, Vector{Float64}}([-1.0, 2.0, 3.0], [3.0, 0.0, -1.0])

julia> Line([-1.0, 2, 3], [3.0, 0, -1]; normalize=true)
Line{Float64, Vector{Float64}}([-1.0, 2.0, 3.0], [0.9486832980505138, 0.0, -0.31622776601683794])
```

2. The second constructor takes two points, `from` and `to`, as keyword

arguments, and returns the line through them. See the algorithm section for details.

```jldoctest
julia> Line(from=[-1.0, 2, 3], to=[2.0, 2, 2])
Line{Float64, Vector{Float64}}([-1.0, 2.0, 3.0], [3.0, 0.0, -1.0])
```

3. The third constructor resembles `Line2D` and only works for two-dimensional

lines. It takes two inputs, `a` and `b`, and constructs the line such that $a ⋅ x = b$.

```jldoctest
julia> Line([2.0, 0], 1.)
Line{Float64, Vector{Float64}}([0.5, 0.0], [0.0, 1.0])
```

### Algorithm

Given two points $p ∈ ℝ^n$ and $q ∈ ℝ^n$, the line that passes through these two points is `L:`{y ∈ ℝ^n: y = p + λ(q - p), λ ∈ ℝ}``.
