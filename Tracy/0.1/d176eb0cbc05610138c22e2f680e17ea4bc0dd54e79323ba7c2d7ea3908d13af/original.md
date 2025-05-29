```
tracyplot_config(name::String; format::Symbol=:number, step::Bool=false, fill::Bool=true, color::Union{Integer,Symbol,NTuple{3, Integer}, Nothing}=nothing)
```

Configures a plot with the given name. Should typically be called once per plot.

  * The `format` parameter can be one of `:number`, `:memory`, or `:percentage`.
  * The `step` parameter determines whether the plot will be displayed as a staircase or will smoothly change between plot points
  * The `fill` parameter can be used to disable filling the area below the plot with a solid color.

If `color` is `nothing`, the default color is used. Otherwise, the `color` argument can be given as:

  * An integer: The hex code of the color as `0xRRGGBB`.
  * A symbol: Can take the value `:black`, `:blue`, `:green`, `:cyan`, `:red`, `:magenta`, `:yellow`, `:white`, `:light_black`, `:light_blue`, `:light_green`, `:light_cyan`, `:light_red`, `:light_magenta`, `:light_yellow`, `:light_white`.
  * A tuple of three integers: The RGB value `(R, G, B)` where each value is in the range 0..255.

See also: [`tracyplot`](@ref).
