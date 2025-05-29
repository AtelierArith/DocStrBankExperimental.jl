```
surfaceplot(x, y, A; kw...)
surfaceplot!(p, args...; kw...)
```

Draws a 3D surface plot on a new canvas (masking values using `NaN`s is supported). To plot a slice one can pass an anonymous function which maps to a constant height: `zscale = z -> a_constant`. By default, `zscale = :aspect` normalizes heights (`z` axis) to the `x` or `y` axes. The `x`, `y` and `z` axes of the 3D cartesian frame are mapped respectively to the `:red`, `:green` and `:blue` colors.

# Usage

```
surfaceplot(x, y, A; lines = false, canvas = UnicodePlots.BrailleCanvas, title = "", xlabel = "", ylabel = "", zlabel = "", height = 15, width = 40, border = :solid, compact = false, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, colorbar = false, colorbar_border = :solid, colorbar_lim = (0, 1), colormap = :viridis, yflip = false, xflip = false, projection = :orthographic, elevation = 35.264389682754654, azimuth = 45.0, axes3d = true, zoom = 1.0, up = :z, name = "", zlim = (0, 0))
```

# Arguments

  * **`A`** : `Matrix` of surface heights, or `Function` evaluated as `f(x, y)`.
  * **`lines`** : use `lineplot` instead of `scatterplot` (for regular increasing data).
  * **`zscale::Symbol = :aspect`** : scale heights (`:identity`, `:aspect`, tuple of (min, max) values, or arbitrary scale function).
  * **`x`** : horizontal position for each point.
  * **`y`** : vertical position for each point.
  * **`title::String = ""`** : text displayed on top of the plot.
  * **`xlabel::String = ""`** : text displayed on the `x` axis of the plot.
  * **`ylabel::String = ""`** : text displayed on the `y` axis of the plot.
  * **`zlabel::String = ""`** : text displayed on the `z` axis (colorbar) of the plot.
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
  * **`projection::Symbol = :orthographic`** : projection for 3D plots (`:ortho(graphic)`, `:persp(ective)`, or `Model-View-Projection` (MVP) matrix).
  * **`axes3d::Bool = true`** : draw 3d axes (`x -> :red`, `y -> :green`, `z -> :blue`).
  * **`elevation::Float = 35.264389682754654`** : elevation angle above or below the `floor` plane (`-90 ≤ θ ≤ 90`).
  * **`azimuth::Float = 45.0`** : azimutal angle around the `up` vector (`-180° ≤ φ ≤ 180°`).
  * **`zoom::Float = 1.0`** : zooming factor in 3D.
  * **`up::Symbol = :z`** : up vector (`:x`, `:y` or `:z`), prefix with `m -> -` or `p -> +` to change the sign e.g. `:mz` for `-z` axis pointing upwards.

# Author(s)

  * T Bltg (github.com/t-bltg)

# Examples

```julia-repl
julia> sombrero(x, y) = 15sinc(√(x^2 + y^2) / π)
julia> surfaceplot(-8:.5:8, -8:.5:8, sombrero)
    ┌────────────────────────────────────────┐  15 
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ ┌──┐
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡰⡃⢝⢆⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠭⠂⠒⠭⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⣀⣠⣤⣴⣥⡅⣭⣬⣦⣤⣄⣀⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⣤⣖⡻⠝⡪⢒⢵⣥⡫⠇⠼⢝⣬⡮⡒⢕⠫⢟⣲⣤⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⣠⣾⣿⢗⣒⣊⡩⠔⢁⢎⣐⡱⡁⢏⢎⣂⡱⡈⠢⢍⣑⣒⡺⣿⣷⣄⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⣠⣾⡿⠿⣿⣿⣕⣒⣒⣊⣽⣯⡾⠵⠅⠮⠮⢷⣽⣯⣑⣒⣒⣪⣿⣿⠿⢿⣷⣄⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠐⠻⠿⠛⠛⠛⠛⠽⢿⣶⣶⡾⠓⠉⠢⠈⡀⢁⠁⠔⠉⠚⢷⣶⣶⡿⠯⠛⠛⠛⠛⠿⠟⠂⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⢀⠀⠀⠀⠀⠀⠀⠀⠀⠘⠿⣯⣯⣓⢶⣷⡆⣶⣾⡶⣚⣽⣽⠿⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠻⡳⡻⡃⢟⢟⢞⠟⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⢀⡠⠜⠤⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠪⠆⡵⠕⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠊⠁⠀⠀⠀⠀⠉⠂⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ └──┘
    └────────────────────────────────────────┘ -3  
```

# See also

`Plot`, `MVP`, `lineplot`, `scatterplot`, `BrailleCanvas`
