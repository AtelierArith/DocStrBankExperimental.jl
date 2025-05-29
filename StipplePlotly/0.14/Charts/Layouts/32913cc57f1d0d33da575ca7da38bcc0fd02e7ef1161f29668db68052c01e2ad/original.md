```
ErrorBar()
```

---

# Examples

---

```
julia> error_x = ErrorBar(
    array = [1.2, 2.6, 3.1],
    type = "data"
)
```

---

# Properties

---

  * `array::Vector{Float64}` - Sets the data corresponding the length of each error bar. Values are plotted relative to the underlying data.
  * `arrayminus::Vector{Float64}` - Sets the data corresponding the length of each error bar in the bottom (left) direction for vertical (horizontal) bars Values are plotted relative to the underlying data.
  * `color::String` - Sets the stoke color of the error bars.
  * `symmetric::Bool` - Determines whether or not the error bars have the same length in both direction (top/bottom for vertical bars, left/right for horizontal bars.
  * `thickness::Int` - Sets the thickness (in px) of the error bars. Type: greater than or equal to 0. Default: 2
  * `traceref::Int` - Type: Integer greater than or equal to 0. Default: 0
  * `tracerefminus::Int` - Type: Integer greater than or equal to 0. Default: 0
  * `type::String` - Determines the rule used to generate the error bars. If "constant`, the bar lengths are of a constant value. Set this constant in`value`. If "percent", the bar lengths correspond to a percentage of underlying data. Set this percentage in`value`. If "sqrt", the bar lengths correspond to the square of the underlying data. If "data", the bar lengths are set with data set`array`. Type: enumerated , one of ( "percent" | "constant" | "sqrt" | "data" )
  * `value::Float64` - Sets the value of either the percentage (if `type` is set to "percent") or the constant (if `type` is set to "constant") in the case of "constant" `type`. Type: greater than or equal to 0. Default: 10
  * `valueminus::Float64` - Sets the value of either the percentage (if `type` is set to "percent") or the constant (if `type` is set to "constant") corresponding to the lengths of the error bars in the bottom (left) direction for vertical (horizontal) bars. Type: number greater than or equal to 0 | Default: 10
  * `visible::Bool` - Determines whether or not this set of error bars is visible.
  * `width::Int` - Sets the width (in px) of the cross-bar at both ends of the error bars. Type: greater than or equal to 0
