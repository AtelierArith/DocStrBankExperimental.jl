```
setlight(B, 1, Dict("on" => true))
setlight(B, 3, Dict("on" => false))
setlight(B, 2, Dict("on" => true, "sat" => 123, "bri" => 243, "hue" => 123)
```

Set a light by passing a dictionary of settings.

eg Dict{Any,Any}("on" => true, "sat" => 123, "bri" => 123, "hue" => 123), "hue" is from 0 to 65535, "sat" and "bri" are saturation and brightness from 1 to 254, 0 is red, yellow is 12750, green is 25500, blue is 46920, etc.

If keys are omitted, that aspect of the light won't be changed.

Keys are AbstractStrings, values can be numeric and will get converted to AbstractStrings
