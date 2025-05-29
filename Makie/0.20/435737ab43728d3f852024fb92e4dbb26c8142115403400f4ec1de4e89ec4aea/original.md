```
stairs(xs, ys; kwargs...)
```

Plot a stair function.

The `step` parameter can take the following values:

  * `:pre`: horizontal part of step extends to the left of each value in `xs`.
  * `:post`: horizontal part of step extends to the right of each value in `xs`.
  * `:center`: horizontal part of step extends halfway between the two adjacent values of `xs`.

The conversion trait of stem is `PointBased`.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.stairs}` are: 

```
  alpha           1.0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  cycle           [:color]
  depth_shift     0.0f0
  highclip        MakieCore.Automatic()
  inspectable     true
  linestyle       "nothing"
  linewidth       1.5
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  space           :data
  ssao            false
  step            :pre
  transparency    false
  visible         true
```
