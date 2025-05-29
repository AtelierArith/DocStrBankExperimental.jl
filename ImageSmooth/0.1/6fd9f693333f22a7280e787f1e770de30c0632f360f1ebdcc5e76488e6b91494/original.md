```
L0Smooth <: AbstractImageSmoothAlgorithm
L0Smooth(; λ=2e-2, κ=2.0, βmax=1e5)

smooth(img, f::L0Smooth)
smooth!(out, img, f::L0Smooth)
```

Smoothing `img` via L0 gradient minimization to approximate prominent structure in a sparsity-control manner.

# Output

Return `Array{Gray{N0f8}}` for `Gray` input or `Array{RGB{N0f8}}` for `RGB` input.

# Details

Using the strategy of minimizing the L0 norm of image's gradient.

This algorithm works particularly effective for sharpening major edges by  increasing the steepness of amplitude transition while eliminating  low-amplitude structures to some extent. See [1] for more details. 

# Options

The function argument is described in detail below.

## `λ::Float64`

The argument `𝜆` is a weight directly controlling the significance of  the L0 gradient norm term, which must be greater than zero.

A larger `𝜆` makes the smoothed image have very few edges.

Default: 2e-2

## `βmax::Float64`

The argument `βmax` is the upper bound of `𝛽` in [1], which must be greater than 1e4.

In this algorithm, two auxiliary variables `ℎ` and `𝑣` are used to approximate  the solution. A large enough `𝛽` ensures that the alternating optimization strategy  based on introducing auxiliary variables is available.

Default: 1e5

## `κ::Float64`

The argument `𝜅` is the iteraiton rate, which must be larger than 1.0.

This algorithm using an alternating optimization strategy to get the solution. In each iteration, the argument `𝛽` controls the similarity between gradient pair  (𝛥₁𝑆ₚ, 𝛥₂𝑆ₚ) (denoted by $(\partial_x S_p, \partial_y S_p)$ in [1]) and auxiliary pair (ℎₚ, 𝑣ₚ). The argument `𝜅` is used to update `𝛽` as `𝛽 ⟵ 𝜅𝛽`.

Default: 2.0

# Examples

You can use the default arguments for `L0Smooth`, and then use `smooth` to apply  the `AbstractImageSmoothAlgorithm`.

```julia
using TestImages
using ImageSmooth

img = testimage("cameraman")

fₛ = L0Smooth() # using default arguements
imgₛ = smooth(img, fₛ)
```

Manually setting the arguements is also available:

```julia
fₛ = L0Smooth(λ=0.0015, κ=1.05, βmax=2e5) # manually set the arguments
imgₛ = smooth(img, fₛ)
```

See also [`smooth!`](@ref) for in-place operation.

# References

[1] Xu, L., Lu, C., Xu, Y., & Jia, J. (2011, December). Image smoothing via L 0 gradient minimization. In Proceedings of the 2011 SIGGRAPH Asia conference (pp. 1-12). [DOI:10.1145/2024156.2024208](https://doi.org/10.1145/2024156.2024208)
