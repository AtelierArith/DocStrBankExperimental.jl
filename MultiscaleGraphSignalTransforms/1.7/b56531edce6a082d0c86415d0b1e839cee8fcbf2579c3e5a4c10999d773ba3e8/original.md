```
gplot(A, xyz; plotp = true,
      style = :auto, width = 2, color = :blue,
      shape = :none, mwidth = 2, mcolor = color, malpha = 1.0,
      mscolor = color, mswidth = 1, msalpha = 1.0,
      grid::Bool = false, label = "", subplot = 1)
```

GPLOT Plot graph, as in graph theory. GPLOT(A,xyz,...) plots the graph specified by the adjacency matrix A and the node coordinates xyz. GPLOT!(A,xyz,...) adds a plot to `current` one.

### Input Arguments

  * `A::SparseMatrixCSC{Float64,Int}`: the adjacency matrix of a graph `G`
  * `xyz::Matrix{Float64}`: The coordinates array, `xyz`, is an n-by-2 or n-by-3 matrix

with the position for node i in the i-th row, xyz[i,:] = [x[i] y[i]] or xyz[i,:] = [x[i] y[i] z[i]].

  * `plotp::Bool`: if the plot is made (default) or return the X, Y, Z arrays
  * `style::Symbol`: of line; choose from Symbol[:auto,:solid,:dash,:dot,:dashdot] (default: :auto)
  * `width::Number`: of line in pixels (default: 2; fraction, e.g., 0.5 is allowed)
  * `color::Symbol`: of line; choose from Symbol[:white,:blue,:red,:green,...] (default: :blue)
  * `shape::Symbol`: choose from Symbol[:none,:auto,:circle,:rect,:star5,:diamond,                                     :hexagon,:cross,:xcross,:utriangle,                                     :dtriangle,:pentagon,:heptagon,:octagon,                                     :star4,:star6,:star7,:star8,:vline,:hline] (default: :none)
  * `mwidth::Number`: marker size (or radius) in pixels (default: 2)
  * `mcolor::Symbol`: of marker (default: the same as line color)
  * `malpha::Float64`: opacity of marker interior; choose from [0,1] (default: 1.0)
  * `mswidth::Number`: marker stroke size (width) in pixels (default: 1)
  * `mscolor::Symbol`: of marker stroke (default: the same as line color)
  * `msalpha::Float64`: opacity of marker stroke; choose from [0,1] (default: 1.0)
  * `grid::Bool`: a flag to show grid lines (default: false)
  * `label::String`: a string for legend (default: "")
  * `subplot::Int`: subplot index (default: 1)

### Output Arguments

  * `X::Matrix{Float64}`: Nan-punctuated X coordinate vector
  * `Y::Matrix{Float64}`: Nan-punctuated Y coordinate vector
  * `Z::Matrix{Float64}`: Nan-punctuated Z coordinate vector

(X,Y)= GPLOT(A,xyz,plotp=false,...) or (X,Y,Z) = GPLOT(A,xyz,plotp=false,...) return the NaN-punctuated vectors X and Y or X, Y and Z without actually generating a plot. These vectors can be used to generate the plot at a later time with PLOT or PLOT3D if desired.

A backward-compatible elaboration of Mathworks's gplot that uses 3D data (if available) when the plot is rotated. Robert Piche, Tampere Univ. of Tech., 2005

Translated into julia by Naoki Saito, Dec. 21, 2016. Note that we should still consider the keywords organized as `function gplot(A,xyz,kw...)`

Nicholas Hausch edits: Must install Plots package For 3D rotation, use `plotlyjs()` backend

Revised by Naoki Saito, Feb. 17, 2017 Revised by Naoki Saito, Oct. 13, 2017 Revised by Haotian Li, Jul. 25, 2018 Revised by Haotian Li and Naoki Saito for Julia v0.7/1.0, Sep. 21, 2018 Instead of plot(...), we decided to use Plots.plot(...) in order to avoid     the function name ambiguity; this is a safer approach. Revised by Naoki Saito, Oct. 22, 2018
