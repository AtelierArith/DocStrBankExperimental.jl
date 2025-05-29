**`Makie.SliderGrid <: Block`**

A grid of one or more horizontal `Slider`s, where each slider has a name label on the left and a value label on the right.

Each `NamedTuple` you pass specifies one `Slider`. You always have to pass `range` and `label`, and optionally a `format` for the value label. Beyond that, you can set any keyword that `Slider` takes, such as `startvalue`.

The `format` keyword can be a `String` with Format.jl style, such as "{:.2f}Hz", or a function.

## Constructors

```julia
SliderGrid(fig_or_scene, nts::NamedTuple...; kwargs...)
```

## Examples

```julia
sg = SliderGrid(fig[1, 1],
    (label = "Amplitude", range = 0:0.1:10, startvalue = 5),
    (label = "Frequency", range = 0:0.5:50, format = "{:.1f}Hz", startvalue = 10),
    (label = "Phase", range = 0:0.01:2pi,
        format = x -> string(round(x/pi, digits = 2), "π"))
)
```

Working with slider values:

```julia
on(sg.sliders[1].value) do val
    # do something with `val`
end
```

**Attributes**

(type `?Makie.SliderGrid.x` in the REPL for more information about attribute `x`)

`alignmode`, `halign`, `height`, `tellheight`, `tellwidth`, `valign`, `value_column_width`, `width`
