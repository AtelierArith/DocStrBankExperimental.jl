```
∂log(Z::Rotor)
```

Return the gradient of `log(Z)` with respect to the components of `Z`.

The result includes "off-shell" components of the gradient, meaning that even though change of `Z` in a direction that changes its norm would not be allowed for a `Rotor`, we measure the gradient in that direction anyway.  That is, the elements of the returned vector of quaternions is

$$
\begin{aligned}
  \left[
    \frac{\partial} {\partial Z_w} \log(Z),
    \frac{\partial} {\partial Z_x} \log(Z),
    \frac{\partial} {\partial Z_y} \log(Z),
    \frac{\partial} {\partial Z_z} \log(Z)
  \right].
\end{aligned}
$$

Note that, even though `log(::Rotor)` is a `QuatVec`, the derivative (and therefore each element of the result) is a general `Quaternion`.

See also [`∂exp`](@ref) for a similar function, as well as [`log∂log`](@ref) for a function to compute the value along with the gradient.

# Examples

```julia
julia> ∂log∂w, ∂log∂x, ∂log∂y, ∂log∂z = ∂log(randn(QuatVecF64));

```
