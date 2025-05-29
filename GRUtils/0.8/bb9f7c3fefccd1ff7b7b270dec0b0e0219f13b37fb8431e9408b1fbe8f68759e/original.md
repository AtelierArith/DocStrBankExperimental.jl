```
Figure([figsize::Tuple{Float64, Float64}, units::String])
```

Create a new figure of a given size.

The figure size is defined by `figsize` (a 2-tuple with the target width and height), and `units` (a string with the abbreviation of the units: "px" for pixels, "in" for inches, "cm" for centimeters or "m" for meters). The default dimensions used by `Figure()` with no arguments is 600×450 pixels — or a proportional increased size, if the detected display resolution is high. This constructor also sets the "current figure" to the one that has just been created..
