```
create_quadratic_spline(x::Union{Vector{DateTime},Vector{Date},Vector{Union{Date,DateTime}}},y::Vector{<:Real} ; gradients::Union{Missing,Vector{<:Real}} = missing, extrapolation::Tuple{Schumaker_ExtrapolationSchemes,Schumaker_ExtrapolationSchemes} = (Curve,Curve),
                             left_gradient::Union{Missing,Real} = missing, right_gradient::Union{Missing,Real} = missing)
create_quadratic_spline(x::Vector{<:Real},y::Vector{<:Real} ; gradients::Union{Missing,Array{<:Real}} = missing, extrapolation::Tuple{Schumaker_ExtrapolationSchemes,Schumaker_ExtrapolationSchemes} = (Curve,Curve),
                             left_gradient::Union{Missing,Real} = missing, right_gradient::Union{Missing,Real} = missing)
create_quadratic_spline(x::Union{Vector{D},Vector{<:DatePeriod}},y::Vector{<:Real}; gradients::Union{Missing,Vector{<:Real}} = missing, extrapolation::Tuple{Schumaker_ExtrapolationSchemes,Schumaker_ExtrapolationSchemes} = (Curve,Curve),
                             left_gradient::Union{Missing,Real} = missing, right_gradient::Union{Missing,Real} = missing) where D<:DatePeriod
```

Makes a quadratic shape-preserving interpolation spline using the SchumakerSpline.jl package. This is returned as a `Piecewise_Function` rather than as a `Schumaker` struct.

### Inputs

  * `x` - A `Vector` with the x coordinates
  * `y` - A `Vector` with the y coordinates
  * `gradients` - A `Vector` with the gradiants at each x location. This is calculated if not provided.
  * `extrapolation` - A tuple of enum value describing how to extrapolate (on the left and right sides).
  * `left_gradient` - The gradiant to impose on the left edge (ie the first x coordinate).
  * `right_gradient` - The gradiant to impose on the right edge (ie the last x coordinate).

### Returns

  * A `Piecewise_Function` containing the spline.

```
create_quadratic_spline(schum::Schumaker)
```

This converts a spline represented by a `SchumakerSpline.Schumaker` struct into the same spline but represented by a `Piecewise_Function`.

### Inputs

  * `schum` - A `Schumaker` struct.

### Returns

  * A `Piecewise_Function` containing the spline.
