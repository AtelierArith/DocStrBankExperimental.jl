```
contourplot(x, y, A; kw...)
contourplot!(p, args...; kw...)
```

Draws a contour plot on a new canvas.

# Usage

```
contourplot(x, y, A; canvas = UnicodePlots.BrailleCanvas, title = "", xlabel = "", ylabel = "", zlabel = "", xscale = :identity, yscale = :identity, height = 15, width = 40, border = :solid, compact = false, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, colorbar = false, colorbar_border = :solid, colorbar_lim = (0, 1), colormap = :viridis, yflip = false, xflip = false, name = "", zlim = (0, 0))
```

# Arguments

  * **`A`** : `Matrix` of interest for which contours are extracted, or `Function` evaluated as `f(x, y)`.
  * **`levels`** : the number of contour levels.
  * **`x`** : horizontal position for each point.
  * **`y`** : vertical position for each point.
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
  * **`canvas::UnionAll = UnicodePlots.BrailleCanvas`** : type of canvas used for drawing.
  * **`compact::Bool = false`** : compact plot labels.
  * **`unicode_exponent::Bool = true`** : use `Unicode` symbols for exponents: e.g. `10²⸱¹` instead of `10^2.1`.

# Author(s)

  * T Bltg (github.com/t-bltg)

# Examples

```julia-repl
julia> contourplot(-1:.1:1, -1:.1:1, (x, y) -> 1000√(x^2 + y^2))
      ┌────────────────────────────────────────┐ 1_000
    1 │⠀⠀⠀⠀⠀⠀⠀⠀⣀⠤⠒⠊⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠉⠒⠢⣄⡀⠀⠀⠀⠀⠀⠀⠀│ ┌──┐ 
      │⠀⠀⠀⠀⠀⡠⠖⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠑⠤⡀⠀⠀⠀⠀│ │▄▄│ 
      │⠀⠀⢀⡰⠊⠀⠀⠀⠀⠀⠀⠀⢀⣀⠤⠔⠒⠒⠉⠉⠉⠉⠓⠒⠒⠤⣄⡀⠀⠀⠀⠀⠀⠀⠀⠘⠢⡀⠀⠀│ │▄▄│ 
      │⠀⡰⠁⠀⠀⠀⠀⠀⠀⢀⡤⠒⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠑⠢⡀⠀⠀⠀⠀⠀⠀⠈⢆⠀│ │▄▄│ 
      │⡜⠀⠀⠀⠀⠀⠀⢀⠔⠁⠀⠀⠀⠀⠀⠀⠀⢀⣀⣀⣀⣀⡀⠀⠀⠀⠀⠀⠀⠀⠈⠢⡄⠀⠀⠀⠀⠀⠀⢣│ │▄▄│ 
      │⠀⠀⠀⠀⠀⠀⢠⠃⠀⠀⠀⠀⠀⠀⢀⠔⠊⠁⠀⠀⠀⠀⠈⠙⠢⢄⠀⠀⠀⠀⠀⠀⠑⡄⠀⠀⠀⠀⠀⠀│ │▄▄│ 
      │⠀⠀⠀⠀⠀⢠⠇⠀⠀⠀⠀⠀⠀⡜⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢣⠀⠀⠀⠀⠀⠀⢘⠄⠀⠀⠀⠀⠀│ │▄▄│ 
      │⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠠⡃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢈⠆⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀│ │▄▄│ 
      │⠀⠀⠀⠀⠀⠘⡆⠀⠀⠀⠀⠀⠀⠣⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡜⠀⠀⠀⠀⠀⠀⢠⠃⠀⠀⠀⠀⠀│ │▄▄│ 
      │⠀⠀⠀⠀⠀⠀⠱⡀⠀⠀⠀⠀⠀⠀⠉⠒⣄⣀⠀⠀⠀⠀⢀⣀⠔⠉⠀⠀⠀⠀⠀⠀⢀⠎⠀⠀⠀⠀⠀⠀│ │▄▄│ 
      │⢇⠀⠀⠀⠀⠀⠀⠘⠦⡀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠉⠉⠉⠁⠀⠀⠀⠀⠀⠀⠀⠀⡠⠃⠀⠀⠀⠀⠀⠀⡰│ │▄▄│ 
      │⠈⠢⡀⠀⠀⠀⠀⠀⠀⠈⠒⠤⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⡠⠔⠋⠀⠀⠀⠀⠀⠀⢀⠖⠁│ │▄▄│ 
      │⠀⠀⠈⠱⣀⠀⠀⠀⠀⠀⠀⠀⠈⠉⠒⠢⠤⢤⣀⣀⣀⣀⡠⠤⠤⠒⠊⠁⠀⠀⠀⠀⠀⠀⠀⢀⠔⠁⠀⠀│ │▄▄│ 
      │⠀⠀⠀⠀⠀⠑⠦⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⡠⠒⠁⠀⠀⠀⠀│ │▄▄│ 
   -1 │⠀⠀⠀⠀⠀⠀⠀⠀⠙⠒⠤⢄⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⣀⠤⠔⠊⠁⠀⠀⠀⠀⠀⠀⠀│ └──┘ 
      └────────────────────────────────────────┘  0   
      ⠀-1⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀1⠀      
```

# See also

`Plot`, `lineplot`, `BrailleCanvas`
