```
slerp∂slerp(q₁, q₂, τ)
```

Return the value and gradient of `slerp`.

The gradient is with respect to each of the input arguments in turn, with each quaternion regarded as a series of four arguments.  That is, a total of 10 quaternions will be returned:

$$
\begin{aligned}
  &\big[\\
    &\quad \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₁.w} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₁.x} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₁.y} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₁.z} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₂.w} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₂.x} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₂.y} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₂.z} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial \tau} \mathrm{slerp}(q₁, q₂, τ), \\
  &\big]
\end{aligned}
$$

For convenience, this will be a 4-tuple with the `slerp` as the first element, the first four components of the derivative, followed by the next four components of the derivative, followed by the last component of the derivative.

See also [`slerp`](@ref) for just the value, and [`slerp∂slerp∂τ`](@ref) for just the value and the derivative with respect to `τ`.

# Examples

```julia
julia> (q1, q2), τ = randn(RotorF64, 2), rand();

julia> s, ∂s∂q₁, ∂s∂q₂, ∂s∂τ = slerp∂slerp(q₁, q₂, τ);

```
