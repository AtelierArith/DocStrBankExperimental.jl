```
G = GraphSig(W, xy, f, name, plotspecs, length, dim, size)
```

is a data structure for a GraphSig object containing the following fields:

  * `W::SparseMatrixCSC{Float64,Int}`: the edge weight matrix in a sparse format
  * `xy::Matrix{Float64}`: the coordinates of the vertices (could be >= 3D)
  * `f::Matrix{Float64}`: the values of the function/data at the vertices; each column is an input signal vector, i.e., number of rows == number of nodes.
  * `name::String`: a title/name for the data
  * `plotspecs::Vector{Symbol}`: specifications for plotting:   (most likely may be dropped later thanks to julia/Plots.jl)                  - symm: use a symmetric colorscale                  - gray: use grayscale                  - gray255: plot a grayscale image with color bounds [0,255]                  - copper: use a copper color scale                  - notitle: don't display the title                  - nocolorbar: don't display a colorbar                  - stem: use a stem plot                  - CLim[cmin,cmax]: set the dynamic display range to [cmin,cmax]                  - size25: set the size of the nodes to 25 (or whatever value is specified)                  - LineWidth2: set the width of the lines to 2 (or whatever value is specified)                  - LineColorb: set the color of the lines/graph edges to color 'b' (or whatever color is specified)                  - red/black/blue: make the nodes red, black, or blue                  - verbatim{{...}}: execute the command in the brackets
