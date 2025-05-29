```
boxplot(data; kw...)
boxplot!(p, args...; kw...)
```

# Description

Draws a box-and-whisker plot.

The first argument specifies the data to plot. This is a vector of vectors, with each inner vector representing a data series. We use a vector of vectors over a matrix to allow series of different lengths. Optionally, a list of text may be provided, with length equal to the number of series.

Alternatively, one can specify a boxplot using a dictionary. In that case, the values, which have to be numeric, will be used as the data series, and the keys, which have to be strings, will be used as the labels.

# Usage

```
boxplot([text], data; border = :corners, color = :green, title = "", xlabel = "", ylabel = "", xscale = :identity, yscale = :identity, width = 40, compact = false, blend = true, xlim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, yflip = false, xflip = false, name = "")
boxplot(dict; kw...)
```

# Arguments

  * **`text`** : the labels/captions of the boxes (optional).
  * **`data`** : a vector of vectors, with each inner vector representing a data series (choose a vector of vectors over a matrix to allow series of different lengths).
  * **`dict`** : a dictionary in which the keys will be used as `text` and the values will be used as `data`.
  * **`color::Symbol = :auto`** : `Vector` of colors, or scalar - choose from (`:green`, `:blue`, `:red`, `:yellow`, `:cyan`, `:magenta`, `:white`, `:normal`, `:auto`), use an integer in `[0-255]`, or provide `3` integers as `RGB` components.
  * **`title::String = ""`** : text displayed on top of the plot.
  * **`name::String = ""`** : current drawing annotation displayed on the right.
  * **`xlabel::String = ""`** : text displayed on the `x` axis of the plot.
  * **`ylabel::String = ""`** : text displayed on the `y` axis of the plot.
  * **`xscale::Symbol = :identity`** : `x`-axis scale (`:identity`, `:ln`, `:log2`, `:log10`), or scale function e.g. `x -> log10(x)`.
  * **`labels::Bool = true`** : show plot labels.
  * **`border::Symbol = :solid`** : plot bounding box style (`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`).
  * **`margin::Int = 3`** : number of empty characters to the left of the whole plot.
  * **`padding::Int = 1`** : left and right space between the labels and the canvas.
  * **`width::Int = 40`** : number of characters per canvas row, or `:auto`.
  * **`xlim::Tuple = (0, 0)`** : plotting range for the `x` axis (`(0, 0)` stands for automatic).
  * **`xflip::Bool = false`** : set `true` to flip the `x` axis.
  * **`yflip::Bool = false`** : set `true` to flip the `y` axis.
  * **`compact::Bool = false`** : compact plot labels.
  * **`unicode_exponent::Bool = true`** : use `Unicode` symbols for exponents: e.g. `10²⸱¹` instead of `10^2.1`.
  * **`blend::Bool = true`** : blend colors on the underlying canvas.

# Author(s)

  * Matthew Lake (github.com/mgtlake)

# Examples

```julia-repl
julia> boxplot([1, 2, 3, 7]; title = "Test")
                       Test                    
    ┌                                        ┐ 
     ╷   ┌────┬─────────┐                   ╷  
     ├───┤    │         ├───────────────────┤  
     ╵   └────┴─────────┘                   ╵  
    └                                        ┘ 
     1                  4                   7  
```

# See also

[`Plot`](@ref), [`histogram`](@ref), [`BoxplotGraphics`](@ref)
