```
InteractModel(f, model)
```

An [`AbstractModel`](@ref) that generates its own Interact.jl interface. Each model [`Param`](@ref) has a slider generated for it to update the model. After any slider updates the user-defined function `f` is passed the updated model to generate a new output - anything that will display in a WebIO.jl node, like a Plots.jl plot

After any slider changes, the parent model is updated, so that `parent(model)` will return it's latest state.

## Arguments

  * `f`: a function that take the model object as an argument, but with `Param` fields replaced with their values. Usually a `do` block.
  * `model`: any object with [`Param`](@ref)s objects in some fields.

## Param fields

`Param` objects in the model need to include a `range` or `bounds` field to define the slider range - holding an `AbsractRange` or `NTuple{2}`, respectively.

Optionally, the `Param`s can also include:

  * A `label` field to use instead of field names
  * A `desciption` field to use in mouse hover text

## Keyword Arguments

  * `title`: `""` set a window title, if you need it.
  * `submodel`: `Nothing`. `Type` or `Union` that will group sliders into labeled subsections.
  * `throttle`: `0.1`. Slider throttle, in seconds. Adjust to improve performance.
  * `layout`: `vbox`. This can be any three-argument function that will combine title, output, and sliders (all WebIO nodes) into a combined WebIO node. You can use this method to do any additional layout you need.

## Example

This is a simple example where the model is a `NamedTuple`, adapted from an Interact.jl example. It will display in atoms plot pane:

```julia
using InteractModels, Interact, ColorSchemes, Colors

color(i) = Colors.hex(colors[i%length(colors)+1])
colors = ColorSchemes.viridis
width, height = 700, 300
nsamples = 256

model = (;
    sample_step=Param(val=0.05, range=0.01:0.001:0.1, label="Sample step"),
    phase=Param(val=0.0, range=0:0.1:2pi, label="Phase"),
    radii=Param(val=20,range=0:0.1:60, label="Radus")
)

ui = InteractModel(model; submodel=Nothing, throttle=0.1) do m
    cxs_unscaled = [i * m.sample_step + m.phase for i in 1:nsamples]
    cys = sin.(cxs_unscaled) .* height/3 .+ height/2
    cxs = cxs_unscaled .* width/4pi
    c = (dom"svg:circle[cx=$(cxs[i]), cy=$(cys[i]), r=$(m.radii), fill=#$(color(i))]"()
         for i in 1:nsamples)
    return dom"svg:svg[width=$width, height=$height]"(c...)
end
```
