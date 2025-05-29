```
∂exp(Z::QuatVec)
```

Return the gradient of `exp(Z)` with respect to the components of `Z`.

The result includes "off-shell" components of the gradient, meaning that even though a scalar component of `Z` would not be allowed for a `QuatVec`, we measure the gradient in that direction anyway.  That is, the first element of the returned vector of quaternions is

$$
\begin{aligned}
  \left.\frac{\partial} {\partial Z_w} \exp(Z) \right|_{Z_w=0}.
\end{aligned}
$$

Note that, even though `exp(::QuatVec)` is a `Rotor`, the derivative (and therefore each element of the result) is a general `Quaternion`.

See also [`∂log`](@ref) for a similar function, as well as [`exp∂exp`](@ref) for a function to compute the value along with the gradient.

# Examples

```julia
julia> ∂exp∂w, ∂exp∂x, ∂exp∂y, ∂exp∂z = ∂exp(randn(QuatVecF64));

```
