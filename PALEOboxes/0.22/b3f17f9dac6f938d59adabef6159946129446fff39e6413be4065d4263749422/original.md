```
function set_coordinates!(obj, dimname, coordinates::Vector{String})
```

Set coordinates (variable names) attached to `dimname` for PALEO object `obj`

PALEO convention is that where possible `coordinates` contains:

  * three variable names, for cell midpoints, lower edges, upper edges, in that order.
  * two variable names, for cell midpoints and a bounds variable (with a bounds dimension as the first dimensions)
