```
y = cumtrapz(Δt, x)
```

Trapezoidal cumulative integration over time for every spin of a phantom.

# Arguments

  * `Δt`: (`1 x NΔt ::Matrix{Float64}`, `[s]`) delta time 1-row array
  * `x`: (`Ns x (NΔt+1) ::Matrix{Float64}`, `[T]`) magnitude of the field Gx * x + Gy * y +   Gz * z

# Returns

  * `y`: (`Ns x NΔt ::Matrix{Float64}`, `[T*s]`) matrix where every column is the   cumulative integration over time of (Gx * x + Gy * y + Gz * z) * Δt for every spin of a   phantom
