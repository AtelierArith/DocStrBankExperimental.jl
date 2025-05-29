```
Plot(graphics; kw...)
```

# Description

Decoration for objects that are `GraphicsArea` (or `Canvas`). It is used to surround the inner `GraphicsArea` object with additional information such as a title, border, and axis labels.

# Usage

```
Plot(graphics; title = "", xlabel = "", ylabel = "", zlabel = "", border = :solid, compact = false, margin = 3, padding = 1, labels = true)

Plot(x, y, z, canvas; title = "", xlabel = "", ylabel = "", xscale = :identity, yscale = :identity, height = 15, width = 40, border = :solid, compact = false, blend = true, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, grid = true, yflip = false, xflip = false, name = "")
```

# Arguments

  * **`graphics`** : the `GraphicsArea` (e.g. a subtype of `Canvas`) that the plot should decorate.
  * **`x`** : horizontal position for each point.
  * **`y`** : vertical position for each point.
  * **`z`** : depth position for each point.
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
  * **`canvas::UnionAll = UnicodePlots.BrailleCanvas`** : type of canvas used for drawing.
  * **`grid::Bool = true`** : draws grid-lines at the origin.
  * **`compact::Bool = false`** : compact plot labels.
  * **`unicode_exponent::Bool = true`** : use `Unicode` symbols for exponents: e.g. `10²⸱¹` instead of `10^2.1`.
  * **`blend::Bool = true`** : blend colors on the underlying canvas.

# Methods

  * `title!(plot::Plot, title::String)`
  * `xlabel!(plot::Plot, xlabel::String)`
  * `ylabel!(plot::Plot, xlabel::String)`
  * `zlabel!(plot::Plot, zlabel::String)`
  * `label!(plot::Plot, where::Symbol, value::String)`
  * `label!(plot::Plot, where::Symbol, row::Integer, value::String)`

Author(s)

  * Christof Stocker (github.com/Evizero)

# See also

[`scatterplot`](@ref), [`lineplot`](@ref), [`BarplotGraphics`](@ref), [`BrailleCanvas`](@ref), [`BlockCanvas`](@ref), [`AsciiCanvas`](@ref)
