```
tracymsg(msg::AbstractString; color::Union{Integer,Symbol,NTuple{3, Integer}, Nothing}=nothing, callstack_depth::Integer=0)
```

Send a message to Tracy that gets shown in the "Message" window. If `color` is `nothing`, the default color is used. Otherwise, the `color` argument can be given as:

  * An integer: The hex code of the color as `0xRRGGBB`.
  * A symbol: Can take the value `:black`, `:blue`, `:green`, `:cyan`, `:red`, `:magenta`, `:yellow`, `:white`, `:light_black`, `:light_blue`, `:light_green`, `:light_cyan`, `:light_red`, `:light_magenta`, `:light_yellow`, `:light_white`.
  * A tuple of three integers: The RGB value `(R, G, B)` where each value is in the range 0..255.

The `callstack_depth` argument determines the depth of the callstack that is collected.
