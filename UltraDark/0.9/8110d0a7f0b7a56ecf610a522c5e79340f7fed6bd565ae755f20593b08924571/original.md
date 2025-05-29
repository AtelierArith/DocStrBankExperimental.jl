```julia
struct Grids <: UltraDark.AbstractGrids
```

```
Grids(length, resol::Int)
Grids(length_tuple, resol_tuple::Tuple{Int, Int, Int})
```

struct containing grids used in a simulation

# Fields

  * `x::Array{Float64, 3}`: Array of x positions
  * `y::Array{Float64, 3}`: Array of y positions
  * `z::Array{Float64, 3}`: Array of z positions
  * `kx::Array{Float64, 3}`: Array of x Fourier modes
  * `ky::Array{Float64, 3}`: Array of y Fourier modes
  * `kz::Array{Float64, 3}`: Array of z Fourier modes
  * `k::Array{Float64, 3}`: Fourier space postition array
  * `rkx::Array{Float64, 3}`: Array of x Fourier modes for use with `rfft`
  * `rky::Array{Float64, 3}`: Array of y Fourier modes for use with `rfft`
  * `rkz::Array{Float64, 3}`: Array of z Fourier modes for use with `rfft`
  * `rk::Array{Float64, 3}`: Fourier space postition array for use with `rfft`
  * `ψx::Array{ComplexF64, 3}`: ψ field
  * `ψk::Array{ComplexF64, 3}`: ψ field in Fourier space
  * `ρx::Array{Float64, 3}`: density field ρ
  * `ρk::Array{ComplexF64, 3}`: density field ρ in Fourier space
  * `Φx::Array{Float64, 3}`: gravitational potential field Φ
  * `Φk::Array{ComplexF64, 3}`: gravitational potential field Φ in fourier space
  * `fft_plan::Any`: FFT plan for complex-to-complex transforms
  * `rfft_plan::Any`: FFT plan for real-to-complex transforms
  * `k_vanish_indices::Vector{CartesianIndex{3}}`: Indices at which k==0.0
  * `rk_vanish_indices::Any`: Indices at which rk==0.0

# Examples

Create an empty grid with length `length` and resolution `resol`

```jldoctest
julia> using UltraDark

julia> length = 1;

julia> resol = 16;

julia> Grids(length, resol);

julia> size(ans.ψx)
(16, 16, 16)
```

Create an empty `length[1]`x`length[2]`x`length[3]` grid with resolution `resol[1]`x`resol[2]`x`resol[3]`.

```jldoctest
julia> using UltraDark

julia> Grids((1.0, 1.0, 0.5), (64, 64, 32));

julia> size(ans.ψx)
(64, 64, 32)
```
