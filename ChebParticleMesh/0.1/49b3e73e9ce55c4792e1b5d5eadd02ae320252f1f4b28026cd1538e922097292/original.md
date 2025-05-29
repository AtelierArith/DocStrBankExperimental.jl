function GridInfo(N*real::NTuple{N, Int}, w::NTuple{N, Int}, periodicity::NTuple{N, Bool}, extra*pad::NTuple{N, Int}, L::NTuple{N, T}) where{N, T<:Union{Float32, Float64}}

```
This function creates a GridBox object with two mutable Array.

N_real: the number of real grid points in each direction
w: the number of grid points in each direction for the window function cutoff
periodicity: a tuple of three boolean values indicating whether the grid is periodic in each direction, to decide padding or not
extra_pad: the number of extra grid points in each direction for padding
L: the length of the box in each direction
h: the grid spacing in each direction, the first point is at [h/2, 3h/2, ..., L - h/2]
N_image: the number of grid points in each direction for the image grid, given by tuple([2 * w[i] + 2 for i in 1:N]...) .+ N_real
N_pad: the numer of padded grid points in each direction, given by tuple([2 * pad[i] * (periodicity[i] == false) for i in 1:N]...) .+ N_image .+ N_real
```
