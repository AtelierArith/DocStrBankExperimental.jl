```
HasTimeAxis{AA}
```

A trait for testing whether type `AA` has a time axis. Time axes must be declared before use.

# Examples

```julia
using ImageAxes, SimpleTraits

# Declare that all axes named `:time` are time axes
@traitimpl TimeAxis{Axis{:time}}

# Define functions that dispatch on AxisArrays that may or may not have time axes
@traitfn got_time{AA<:AxisArray;  HasTimeAxis{AA}}(img::AA) = "yep, I've got time"
@traitfn got_time{AA<:AxisArray; !HasTimeAxis{AA}}(img::AA) = "no, I'm too busy"

julia> A = AxisArray(1:5, Axis{:time}(1:5));

julia> got_time(A)
"yep, I've got time"

julia> A = AxisArray(1:5, Axis{:x}(1:5));

julia> got_time(A)
"no, I'm too busy"
```
