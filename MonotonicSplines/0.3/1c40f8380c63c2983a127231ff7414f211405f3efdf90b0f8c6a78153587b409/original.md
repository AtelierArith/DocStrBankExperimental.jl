struct InvRQSpline{T<:Real,N,...} <: Function

Represents the inverse of [`RQSpline`](@ref).

`InvRQSpline` holds the same spline knot parameters as the corresponding `RQSpline`.

Users should not instantiate `InvRQSpline` directly, use `InverseFunctions.inverse(RQSpline(...))` instead.
