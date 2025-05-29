```
y_at_Τ = interpolate(data, Τ)
```

interpolate a data frame containing a time series characterizing $y(t)$, with `:t` and `:output` columns, whose rows are $(t_i, y(t_i))$ pairs. interpolate the data to approximate the function $y(t)$ at a new time `Τ`, i.e. $y(\Tau)$.

[`simulate`](@ref) returns such a data frame, thus `interpolate` is useful for obtaining the solution at a particular time `Τ` that is not necessarily present in the `:t` column of `data`.

# arguments

  * `data::DataFrame`: a data frame of a time series, containing a `:t` column for times and `:output` column for outputs.
  * `Τ::Float64`: the new time at which we wish to know $y$. i.e. we wish to know $y(\Tau)$.

# Returns

  * `y_at_Τ::Float64`: the value of $y$ when $t$ is equal to `Τ`, $y(\Tau)$, according to linear interpolation.

# example

the unit step response of a first-order process with time constant $\tau$ is $\approx 63\%$ of the final value when $t=\tau$.

```jldoctest
τ = 3.45
g = 1 / (τ * s + 1)           # FO system
U = 1 / s                     # input, U(s)
Y = g * U                     # output, Y(s)
data = simulate(g / s, 10.0)  # output, y(t)
y_at_τ = interpolate(data, τ) # ≈ y(τ)
# output
0.6320802858877126
```
