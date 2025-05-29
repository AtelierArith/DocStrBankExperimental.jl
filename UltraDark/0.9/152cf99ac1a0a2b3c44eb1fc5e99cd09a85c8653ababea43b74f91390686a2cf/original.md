```
PencilGrids(length, resol)
PencilGrids(length_tuple, resol_tuple::Tuple{Int, Int, Int})
```

struct containing grids used in a simulation

Each grid is a `PencilArray`, allowing multiprocess FFTs. This comes with significant overhead so is only useful when running in a multi-node environment.

# Fields

  * `x::Array{Float64, 3}`: Array of x positions
  * `y::Array{Float64, 3}`: Array of y positions
  * `z::Array{Float64, 3}`: Array of z positions
  * `kx::Array{Float64, 3}`: Array of x Fourier modes
  * `ky::Array{Float64, 3}`: Array of y Fourier modes
  * `kz::Array{Float64, 3}`: Array of z Fourier modes
  * `k::Any`: Fourier space postition array
  * `rkx::Array{Float64, 3}`: Array of x Fourier modes for use with `rfft`
  * `rky::Array{Float64, 3}`: Array of y Fourier modes for use with `rfft`
  * `rkz::Array{Float64, 3}`: Array of z Fourier modes for use with `rfft`
  * `rk::Any`: Fourier space postition array for use with `rfft`
  * `ψx::Any`: ψ field
  * `ψk::Any`: ψ field in Fourier space
  * `ρx::Any`: density field ρ
  * `ρk::Any`: density field ρ in Fourier space
  * `Φx::Any`: gravitational potential field Φ
  * `Φk::Any`: gravitational potential field Φ in fourier space
  * `fft_plan::Any`: FFT plan for complex-to-complex transforms
  * `rfft_plan::Any`: FFT plan for real-to-complex transforms
  * `k_vanish_indices::Vector{CartesianIndex{3}}`: Indices at which k==0.0
  * `rk_vanish_indices::Any`: Indices at which rk==0.0
  * `MPI_COMM::Any`: MPI communicator

# Examples

Create an empty grid with length `length` and resolution `resol`.  Uses `PencilFFTs` to create `PencilArrays`.

```jldoctest
julia> using UltraDark

julia> len = 1;

julia> resol = 16;

julia> PencilGrids(len, resol);

```

Create an empty `length[1]`x`length[2]`x`length[3]` grid with resolution `resol[1]`x`resol[2]`x`resol[3]`.

```jldoctest
julia> using UltraDark

julia> PencilGrids((1.0, 1.0, 0.5), (64, 64, 32));

```
