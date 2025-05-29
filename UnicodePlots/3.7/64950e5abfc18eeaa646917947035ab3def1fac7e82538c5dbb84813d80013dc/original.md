```
barplot(text, heights; kw...)
barplot!(p, args...; kw...)
```

# Description

Draws a horizontal barplot. It uses the first parameter (`text`) to denote the names for the bars, and the second parameter (`heights`) as their values. This means that the two vectors have to have the same length. Alternatively, one can specify a barplot using a dictionary `dict`. In that case, the keys will be used as the names and the values, which have to be numeric, will be used as the heights of the bars.

# Usage

```
barplot(text, heights; border = :barplot, color = :green, maximum = nothing, title = "", xlabel = "", ylabel = "", xscale = :identity, width = 40, compact = false, blend = true, margin = 3, padding = 1, labels = true, unicode_exponent = true, yflip = false, xflip = false, symbols = ['■'], name = "")
barplot(dict; kw...)
```

# Arguments

  * **`text`** : the labels / captions of the bars.
  * **`heights`** : the values / heights of the bars.
  * **`dict`** : a dictionary in which the keys will be used as `text` and the values will be used as `heights`.
  * **`xscale::Symbol = :identity`** : `Function` or `Symbol` to transform the bar length before plotting: this effectively scales the `x`-axis without influencing the captions of the individual bars (use `xscale = :log10` for logscale).
  * **`color::Symbol = :auto`** : `Vector` of colors, or scalar - choose from (`:green`, `:blue`, `:red`, `:yellow`, `:cyan`, `:magenta`, `:white`, `:normal`, `:auto`), use an integer in `[0-255]`, or provide `3` integers as `RGB` components.
  * **`maximum`** : optional maximal height.
  * **`symbols::Array = ['■']`** : collection of characters used to render the bars.
  * **`title::String = ""`** : text displayed on top of the plot.
  * **`name::String = ""`** : current drawing annotation displayed on the right.
  * **`xlabel::String = ""`** : text displayed on the `x` axis of the plot.
  * **`ylabel::String = ""`** : text displayed on the `y` axis of the plot.
  * **`labels::Bool = true`** : show plot labels.
  * **`border::Symbol = :solid`** : plot bounding box style (`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`).
  * **`margin::Int = 3`** : number of empty characters to the left of the whole plot.
  * **`padding::Int = 1`** : left and right space between the labels and the canvas.
  * **`width::Int = 40`** : number of characters per canvas row, or `:auto`.
  * **`xflip::Bool = false`** : set `true` to flip the `x` axis.
  * **`yflip::Bool = false`** : set `true` to flip the `y` axis.
  * **`compact::Bool = false`** : compact plot labels.
  * **`unicode_exponent::Bool = true`** : use `Unicode` symbols for exponents: e.g. `10²⸱¹` instead of `10^2.1`.
  * **`blend::Bool = true`** : blend colors on the underlying canvas.

# Author(s)

  * Christof Stocker (github.com/Evizero)

# Examples

```julia-repl
julia> barplot(["Paris", "New York", "Madrid"],
               [2.244, 8.406, 3.165],
               xlabel = "population [in mil]")
            ┌                                        ┐ 
      Paris ┤■■■■■■■■■ 2.244                           
   New York ┤■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■ 8.406   
     Madrid ┤■■■■■■■■■■■■ 3.165                        
            └                                        ┘ 
                        population [in mil]            
```

# See also

[`Plot`](@ref), [`histogram`](@ref), [`BarplotGraphics`](@ref)
