```
spy(A; kw...)
```

# Description

Plots the sparsity pattern for the given matrix `A`. This means that a scatterplot that resembles the matrix is drawn, in which only the pixel for non-zero elements of the matrix are set.

If the parameters `width` and `height` are not explicitly specified, then the function will attempt to preserve the aspect ratio of the matrix, while also attempting to fit the resulting plot within the bounding box specified by `maxwidth` and `maxheight`.

# Usage

```
spy(A; maxwidth = 0, maxheight = 0, zeros = false, canvas = UnicodePlots.BrailleCanvas, title = "", xlabel = "", ylabel = "", xscale = :identity, yscale = :identity, height = 15, width = 40, border = :solid, compact = false, blend = true, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, grid = true, yflip = false, xflip = false, name = "", fix_ar = false)
```

# Arguments

  * **`A`** : matrix of interest for which non-zero elements should be drawn.
  * **`maxheight`** : maximum number of character rows that should be used for plotting.
  * **`maxwidth`** : maximum number of characters per row that should be used for plotting.
  * **`height::Int = 15`** : exact number of character rows that should be used for plotting (`0` stands for automatic).
  * **`width::Int = 40`** : exact number of characters per row that should be used for plotting (`0` stands for automatic).
  * **`show_zeros`** : show zeros pattern instead of default nonzeros.
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
  * **`xlim::Tuple = (0, 0)`** : plotting range for the `x` axis (`(0, 0)` stands for automatic).
  * **`ylim::Tuple = (0, 0)`** : plotting range for the `y` axis.
  * **`xflip::Bool = false`** : set `true` to flip the `x` axis.
  * **`yflip::Bool = false`** : set `true` to flip the `y` axis.
  * **`canvas::UnionAll = UnicodePlots.BrailleCanvas`** : type of canvas used for drawing.
  * **`grid::Bool = true`** : draws grid-lines at the origin.
  * **`compact::Bool = false`** : compact plot labels.
  * **`unicode_exponent::Bool = true`** : use `Unicode` symbols for exponents: e.g. `10²⸱¹` instead of `10^2.1`.
  * **`blend::Bool = true`** : blend colors on the underlying canvas.
  * **`fix_ar::Bool = false`** : fix terminal aspect ratio (experimental).

# Author(s)

  * Dominique Orban (github.com/dpo)
  * Christof Stocker (github.com/Evizero)
  * Jake Bolewski (github.com/jakebolewski)

# Examples

```julia-repl
julia> using SparseArrays
julia> spy(sprandn(50, 120, .05))
      ┌────────────────────────────────────────────────────────────┐    
    1 │⡀⠨⠂⠀⠠⠀⠠⠀⠀⠀⠂⠀⡀⠂⠀⠀⠰⠈⠈⠂⡀⠀⠀⠀⠀⠐⠀⡀⡀⠀⠀⢄⡀⠀⠀⠠⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢄⠀⠀⠀⠁⠀⠀⠀⠀⠀⠀⠐⠴⠄│ > 0
      │⠀⠀⠀⢀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠄⠠⠄⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠐⢀⠀⡀⠀⠄⠘⠀⠀⡀⠀⠀⠀⠂⠠⠀⠀⠀⠀⠀⠈⠀⠀⠀⠀⠀⠀⠀⠀│ < 0
      │⠂⠀⠀⠀⠐⠐⠀⠂⠀⡀⠐⢀⠀⠀⠀⠀⡀⠀⠈⠀⠄⠀⠀⠨⠀⠀⠀⠀⠀⠠⠀⢀⠀⠀⠉⠐⠄⠄⠀⠔⠀⠀⠂⠀⢐⠀⠀⠀⡀⠘⢀⠀⠁⠄⠀⠠⠀⠄⠀⠄│    
      │⠀⢀⠀⠀⠀⠀⠀⠠⠀⠂⠀⠄⠀⠘⠈⠌⢀⠀⠀⠀⠐⠀⠁⠀⠀⠀⢀⠀⠀⠠⠀⠁⠄⠀⠀⠀⠂⢀⠀⠀⠀⠀⢀⡁⠀⠀⠂⠠⠀⠀⠀⠀⠀⠊⠁⠀⠀⠀⠀⠄│    
      │⠀⠅⠀⠀⠀⠀⢄⠈⠄⠠⠈⠀⠀⠀⠀⡀⠀⢀⠠⠀⠀⠀⠁⠀⠀⡀⠃⠀⠀⠈⠈⠁⠀⠁⠠⢀⠀⢁⠀⠀⢀⠀⠀⠀⢀⠀⠠⠂⠀⠁⢁⠀⠂⠀⠀⠆⠌⠀⠀⠀│    
      │⠀⠀⠔⠀⠀⠀⠀⢀⠀⠁⢀⠀⠀⠀⠀⠀⡀⠀⠀⠀⠀⡀⠀⠀⠀⡀⠀⠈⠀⠀⠀⡁⠁⠀⠀⠀⠠⠀⠀⠀⠄⡀⠀⠀⠀⠊⠀⠀⠄⠀⠀⠀⠀⠀⠀⠠⠀⠀⠄⠀│    
      │⠀⠀⠀⠀⠐⠀⠀⠀⠀⠀⠁⠀⠀⠀⠀⠅⠄⡀⠀⠀⢂⠂⠄⠑⠀⠀⠀⢄⠀⠀⠠⠂⠁⡀⠀⢠⠈⠀⠂⠀⠀⠄⠀⠀⠀⠄⠀⠀⠃⠂⠀⠄⢀⠀⠀⠀⠀⠀⠀⠀│    
      │⠀⠐⠀⠀⠂⠀⢀⠀⠀⠀⠀⠀⠀⠀⠀⠌⠀⠂⠀⠀⠀⠀⡀⢁⠁⠨⠀⠀⠀⠂⠀⠀⠨⠀⠁⠀⠀⠀⠀⠀⠊⠀⠄⠀⠀⠁⠐⠠⠀⢀⠀⠀⠀⠈⠀⠀⠁⠐⠄⠄│    
      │⢉⠀⢀⠁⠀⠀⠀⠀⠈⠀⠀⠀⠀⠁⠀⠠⠀⠀⠁⠀⠀⠀⡠⠁⠀⠀⠀⠀⠉⠠⡀⠀⠀⠀⢀⡀⠄⠀⠀⠀⠄⠀⠀⠈⠄⠀⠑⠀⠀⠀⠀⠀⠀⠠⠀⡀⡀⠀⠀⠀│    
      │⠅⠈⠈⠀⠀⠀⠀⠄⠀⠀⠀⠀⠀⠀⠀⠂⠀⠀⡄⠀⠀⠄⠀⠀⠠⠀⠀⠠⠈⠀⠂⠢⠈⠀⠀⠀⠄⠀⠀⠐⠀⠀⠀⠀⠀⠀⠀⠠⠀⠀⠀⠀⠀⠀⢀⠤⠀⠀⠀⠀│    
      │⠀⠀⠀⠂⠁⠀⠀⠀⠀⠁⠀⠘⠀⠂⢠⠀⠀⠀⠀⠀⢃⠀⠐⠈⠄⠐⠀⠀⠀⢀⠀⠀⠁⠀⠀⠀⠀⠀⠀⠀⠄⠀⠀⠀⠀⡀⠀⡀⠀⠀⠁⠀⠁⠀⠁⠠⠔⠀⢁⡀│    
   50 │⠀⠀⠀⠀⠀⠀⡀⠀⠀⠀⠐⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠀⠀⠈⠀⠂⠠⠀⠀⠀⠖⠀⠀⠀⠈⠀⠀⠀⠀⠀⡀⠠⠀⢀⠀⠅⠀⠀⠐⠀⠀⠀⠀⠠⠀⠠⠀⠀⢀⠀│    
      └────────────────────────────────────────────────────────────┘    
      ⠀1⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀120⠀    
      ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀315 ≠ 0⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀    
```

# See also

[`Plot`](@ref), [`scatterplot`](@ref), [`BrailleCanvas`](@ref), [`BlockCanvas`](@ref), [`AsciiCanvas`](@ref), [`DotCanvas`](@ref)
