```
densityplot(x, y; kw...)
densityplot!(p, args...; kw...)
```

# Description

Draws a density plot for the given points.

The first vector `x` should contain the horizontal positions for all the points. The second vector `y` should contain the corresponding vertical positions respectively. The two vectors must thus be of the same length and ordering. One can pass an arbitrary `dscale` (`Function` or `Symbol`) for transforming density counts (e.g. peaks damping).

# Usage

```
densityplot(x, y; dscale = :identity, title = "", xlabel = "", ylabel = "", xscale = :identity, yscale = :identity, height = 15, width = 40, border = :solid, compact = false, blend = true, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, yflip = false, xflip = false, name = "")
```

# Arguments

  * **`dscale`** : density scale function.
  * **`x`** : horizontal position for each point.
  * **`y`** : vertical position for each point.
  * **`title::String = ""`** : text displayed on top of the plot.
  * **`name::String = ""`** : current drawing annotation displayed on the right.
  * **`xlabel::String = ""`** : text displayed on the `x` axis of the plot.
  * **`ylabel::String = ""`** : text displayed on the `y` axis of the plot.
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
  * **`xflip::Bool = false`** : set `true` to flip the `x` axis.
  * **`yflip::Bool = false`** : set `true` to flip the `y` axis.
  * **`compact::Bool = false`** : compact plot labels.
  * **`unicode_exponent::Bool = true`** : use `Unicode` symbols for exponents: e.g. `10²⸱¹` instead of `10^2.1`.
  * **`blend::Bool = true`** : blend colors on the underlying canvas.

# Author(s)

  * Christof Stocker (github.com/Evizero)

# Examples

```julia-repl
julia> densityplot(randn(1_000), randn(1_000); title = "Density Plot")
                     Density Plot                
      ┌────────────────────────────────────────┐ 
    4 │                                        │ 
      │                                        │ 
      │                                        │ 
      │                                        │ 
      │          ░        ░░  ░                │ 
      │           ░ ░░░░░░▓▒▒▒░░░░░            │ 
      │            ░▒▒▓▒░▒▒▓▓▓▒▒░░░░           │ 
      │         ░░  ░░▓▓░▓▒█▓▒░░▒░░░           │ 
      │            ░░░▒▒▒░▒▓▒▒▒░░░░░           │ 
      │          ░  ░░░░░▓░░░░░░░ ░            │ 
      │                 ░░░░░ ░  ░             │ 
      │                                        │ 
      │                                        │ 
      │                                        │ 
   -4 │                                        │ 
      └────────────────────────────────────────┘ 
       -4                                     4  
```

# See also

[`Plot`](@ref), [`scatterplot`](@ref), [`DensityCanvas`](@ref)
