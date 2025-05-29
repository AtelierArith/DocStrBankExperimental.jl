```
compute_magnetic_phase(m::Array{T,4}, theta::Real, axis::String;
```

N1::Int=-1, N2::Int=-1, Ms=1/mu_0, d::Real=1.0) where {T<:AbstractFloat}

Compute the magnetic phase from magnetization array.

## Parameters

m: 4D array sized (3, nx, ny, nz). Magnetization array. theta: Euler angle. axis: rotation axis chosen from "X" or "Y" N1: padding size when calculating projection N2: padding size of Fourier transfrom kernel, by default 2*N1

## Outputs

phi: 2D array sized (N,N). Magnetic phase.
