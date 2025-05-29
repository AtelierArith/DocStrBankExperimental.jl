```
heatmap(A; kw...)
```

# Description

Draws a heatmap for the given points. It uses the `Matrix` `A` as the values of the heatmap, with the column and row indices of the matrix as `x` and `y` coordinates respectively.

# Usage

```
heatmap(A::AbstractMatrix; height = 0, width = 0, yfact = nothing, xfact = nothing, array = false, title = "", xlabel = "", ylabel = "", zlabel = "", xscale = :identity, yscale = :identity, border = :solid, compact = false, blend = true, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, colorbar = false, colorbar_border = :solid, colorbar_lim = (0, 1), colormap = :viridis, grid = true, yflip = false, xflip = false, name = "", zlim = (0, 0), fix_ar = false)
```

# Arguments

  * **`A`** : input matrix (color values).
  * **`yfact`** : scale for the `y` coordinate labels (defaults to 0 - i.e. each row in `A` maps to one unit, `y` origin starting at 1). If set to anything else, the y origin will start at 0.
  * **`xfact`** : scale for the `x` coordinate (defaults to 0 - i.e. each column in `A` maps to one unit, `x` origin starting at 1). If set to anything else, the x origin will start at 0.
  * **`yoffset`** : plotting offset for the `y` coordinate (after scaling).
  * **`xoffset`** : plotting offset for the `x` coordinate (after scaling).
  * **`array`** : use array display convention (origin at the North-West corner of the plot, hence flipping `y` versus regular plots).
  * **`title::String = ""`** : text displayed on top of the plot.
  * **`name::String = ""`** : current drawing annotation displayed on the right.
  * **`xlabel::String = ""`** : text displayed on the `x` axis of the plot.
  * **`ylabel::String = ""`** : text displayed on the `y` axis of the plot.
  * **`zlabel::String = ""`** : text displayed on the `z` axis (colorbar) of the plot.
  * **`xscale::Symbol = :identity`** : `x`-axis scale (`:identity`, `:ln`, `:log2`, `:log10`), or scale function e.g. `x -> log10(x)`.
  * **`yscale::Symbol = :identity`** : `y`-axis scale.
  * **`labels::Bool = true`** : show plot labels.
  * **`border::Symbol = :solid`** : plot bounding box style (`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`).
  * **`margin::Int = 3`** : number of empty characters to the left of the whole plot.
  * **`padding::Int = 1`** : left and right space between the labels and the canvas.
  * **`height::Int = 15`** : number of canvas rows, or `:auto`.
  * **`width::Int = 40`** : number of characters per canvas row, or `:auto`.
  * **`xlim::Tuple = (0, 0)`** : plotting range for the `x` axis (`(0, 0)` stands for automatic).
  * **`ylim::Tuple = (0, 0)`** : plotting range for the `y` axis.
  * **`zlim::Tuple = (0, 0)`** : colormap scaled data range.
  * **`xflip::Bool = false`** : set `true` to flip the `x` axis.
  * **`yflip::Bool = false`** : set `true` to flip the `y` axis.
  * **`colorbar::Bool = false`** : toggle the colorbar.
  * **`colormap::Symbol = :viridis`** : choose a symbol from `ColorSchemes.jl` e.g. `:viridis`, or supply a function `f: (z, zmin, zmax) -> Int(0-255)`, or a vector of RGB tuples.
  * **`colorbar_lim::Tuple = (0, 1)`** : colorbar limit.
  * **`colorbar_border::Symbol = :solid`** : color bar bounding box style (`:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`).
  * **`grid::Bool = true`** : draws grid-lines at the origin.
  * **`compact::Bool = false`** : compact plot labels.
  * **`unicode_exponent::Bool = true`** : use `Unicode` symbols for exponents: e.g. `10²⸱¹` instead of `10^2.1`.
  * **`blend::Bool = true`** : blend colors on the underlying canvas.
  * **`fix_ar::Bool = false`** : fix terminal aspect ratio (experimental).

# Author(s)

  * Rowan Katekar (github.com/rjkat)

# Examples

```julia-repl
julia> heatmap(repeat(collect(0:10)', outer=(11, 1)), zlabel="z")
      ┌───────────┐  10   
   11 │▄▄▄▄▄▄▄▄▄▄▄│ ┌──┐  
      │▄▄▄▄▄▄▄▄▄▄▄│ │▄▄│  
      │▄▄▄▄▄▄▄▄▄▄▄│ │▄▄│  
      │▄▄▄▄▄▄▄▄▄▄▄│ │▄▄│ z
      │▄▄▄▄▄▄▄▄▄▄▄│ │▄▄│  
    1 │▄▄▄▄▄▄▄▄▄▄▄│ └──┘  
      └───────────┘  0    
       1        11        
```

# See also

`Plot`, `HeatmapCanvas`
