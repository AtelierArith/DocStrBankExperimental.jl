```
showBand(Hamiltonian::Function; N::Int=51, labels::Bool=true, value::Bool=true, disp::Bool=false, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="Band")
```

This function generates a band structure plot for a given Hamiltonian.

# Arguments

  * `Hamiltonian::Function`: The Hamiltonian function that takes a wave number parameter `k` and returns the corresponding Hamiltonian matrix.
  * `N::Int`: The number of points in the Brillouin zone. Default is 51.
  * `labels::Bool`: Whether to display the labels of the figure. Default is `true`.
  * `value::Bool`: Whether to output the values of the wave number and the energy in the matrix form. Default is `true`.
  * `disp::Bool`: Whether to display the plot. Default is `false`.
  * `png::Bool`: Whether to save the plot as a PNG file. Default is `false`.
  * `pdf::Bool`: Whether to save the plot as a PDF file. Default is `false`.
  * `svg::Bool`: Whether to save the plot as an SVG file. Default is `false`.
  * `filename::String`: The filename for the saved plot. Default is "Band".

# Examples

```julia
julia> H(k) = SSH(k, (0.9, 1.0)) # $N \times N$ Hamiltonian matrix with a wavenumber parameter k
julia> showBand(H)
(k = -3.141592653589793:0.12566370614359174:3.141592653589793, Ene = [-0.09999999999999998 0.09999999999999998; -0.15554271964299698 0.15554271964299698; … ; -0.15554271964299698 0.15554271964299698; -0.09999999999999998 0.09999999999999998])
```
