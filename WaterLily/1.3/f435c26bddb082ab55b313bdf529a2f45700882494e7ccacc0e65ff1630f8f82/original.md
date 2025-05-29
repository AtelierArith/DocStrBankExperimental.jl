```
Simulation(dims::NTuple, u_BC::Union{NTuple,Function}, L::Number;
           U=norm2(u_BC), Δt=0.25, ν=0., ϵ=1, perdir=()
           uλ::nothing, g=nothing, exitBC=false,
           body::AbstractBody=NoBody(),
           T=Float32, mem=Array)
```

Constructor for a WaterLily.jl simulation:

  * `dims`: Simulation domain dimensions.
  * `u_BC`: Simulation domain velocity boundary conditions, either a         tuple `u_BC[i]=uᵢ, i=eachindex(dims)`, or a time-varying function `f(i,t)`
  * `L`: Simulation length scale.
  * `U`: Simulation velocity scale.
  * `Δt`: Initial time step.
  * `ν`: Scaled viscosity (`Re=UL/ν`).
  * `g`: Domain acceleration, `g(i,t)=duᵢ/dt`
  * `ϵ`: BDIM kernel width.
  * `perdir`: Domain periodic boundary condition in the `(i,)` direction.
  * `exitBC`: Convective exit boundary condition in the `i=1` direction.
  * `uλ`: Function to generate the initial velocity field.
  * `body`: Immersed geometry.
  * `T`: Array element type.
  * `mem`: memory location. `Array`, `CuArray`, `ROCm` to run on CPU, NVIDIA, or AMD devices, respectively.

See files in `examples` folder for examples.
