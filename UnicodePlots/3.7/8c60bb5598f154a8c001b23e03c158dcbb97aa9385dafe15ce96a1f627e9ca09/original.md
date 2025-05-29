```
histogram(data; kw...)
```

# Description

Draws a horizontal or vertical histogram of the given `data`, fitted to an `Histogram`.

# Usage

```
histogram(x; nbins, closed = :left, vertical = false, stats = true, border = :barplot, color = :green, title = "", xlabel = "", ylabel = "", compact = false, blend = true, margin = 3, padding = 1, labels = true, unicode_exponent = true, yflip = false, xflip = false, symbols = ['■'], name = "")
```

# Arguments

  * **`x`** : array of numbers for which the histogram should be computed.
  * **`nbins`** : approximate number of bins that should be used.
  * **`closed`** : if `:left` (default), the bin intervals are left-closed $[a, b)$; if `:right`, intervals are right-closed $(a, b]$.
  * **`vertical`** : vertical histogram instead of the default horizontal one.
  * **`stats`** : display statistics (vertical only).
  * **`symbols::Array = ['■']`** : collection of characters used to render the bars.
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
  * **`grid::Bool = true`** : draws grid-lines at the origin.
  * **`compact::Bool = false`** : compact plot labels.
  * **`unicode_exponent::Bool = true`** : use `Unicode` symbols for exponents: e.g. `10²⸱¹` instead of `10^2.1`.
  * **`blend::Bool = true`** : blend colors on the underlying canvas.

# Author(s)

  * Iain Dunning (github.com/IainNZ)
  * Christof Stocker (github.com/Evizero)
  * Kenta Sato (github.com/bicycle1885)

# Examples

```julia-repl
julia> histogram(randn(1_000) * .1, closed=:right, nbins=15)
                  ┌                                        ┐ 
   (-0.3 , -0.25] ┤▎ 1                                       
   (-0.25, -0.2 ] ┤██▉ 17                                    
   (-0.2 , -0.15] ┤█████████▍ 53                             
   (-0.15, -0.1 ] ┤████████████████▎ 92                      
   (-0.1 , -0.05] ┤████████████████████████▋ 141             
   (-0.05,  0.0 ] ┤███████████████████████████████████  200  
   ( 0.0 ,  0.05] ┤█████████████████████████████████▋ 192    
   ( 0.05,  0.1 ] ┤█████████████████████████▏ 143            
   ( 0.1 ,  0.15] ┤████████████████▎ 92                      
   ( 0.15,  0.2 ] ┤███████▊ 45                               
   ( 0.2 ,  0.25] ┤██▋ 15                                    
   ( 0.25,  0.3 ] ┤█▍ 8                                      
   ( 0.3 ,  0.35] ┤▎ 1                                       
                  └                                        ┘ 
                                   Frequency                
julia> histogram(randn(100_000) .* .1, nbins=60, vertical=true, height=10)
         ┌                                             ┐ 
   8_093  ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀▃█▇▃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  
          ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀▅████▆⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  
          ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀▇██████▅⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  
          ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀▅████████▄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  
          ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀▃██████████▃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  
          ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀▂████████████▂⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  
          ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀▂██████████████▃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  
          ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀▁████████████████▃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  
          ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀▁▅██████████████████▅▁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀  
       0  ⠀⠀⠀⠀⠀⠀▁▁▂▃▅██████████████████████▆▃▂▁▁⠀⠀⠀⠀⠀⠀⠀  
         └                                             ┘ 
         ⠀-0.44⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀0.46⠀ 
         ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀μ ± σ: 0.0 ± 0.1⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀ 
```

# See also

[`Plot`](@ref), [`barplot`](@ref), [`BarplotGraphics`](@ref)
