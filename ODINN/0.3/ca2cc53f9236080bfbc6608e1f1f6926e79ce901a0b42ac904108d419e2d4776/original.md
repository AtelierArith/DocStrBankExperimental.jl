```
SIA2D_D_target(; interpolation=:None, n_interp_half=20,
                 prescale=nothing, postscale=nothing)
```

Inversion of general diffusivity as a function of physical parameters.

D(H, ∇S, θ) = H * NN(H, ∇S; θ)

So now we are learning the velocoty field given by D * ∇S. This inversion is similar to learnign the velocity field assuming that this is parallel to the gradient in surface ∇S.

# Arguments

  * `interpolation::Symbol = :None`: Specifies the interpolation method. Options include `:Linear`, `:None`.
  * `n_interp_half::Int = 20`: Half-width of the interpolation stencil. Determines resolution of interpolation.
  * `prescale::Union{Fin, Nothing} = nothing`: Optional prescaling function or factor applied before parametrization. Must be of type `Fin` or `nothing`.
  * `postscale::Union{Fout, Nothing} = nothing`: Optional postscaling function or factor applied after parametrization. Must be of type `Fout` or `nothing`.

# Type Parameters

  * `Fin`: Type of the prescale function or operator.
  * `Fout`: Type of the postscale function or operator.

# Supertype

  * `AbstractSIA2DTarget`: Inherits from the abstract target type for 2D SIA modeling.

# Returns

  * An instance of `SIA2D_D_target` configured with optional scaling and interpolation parameters.
