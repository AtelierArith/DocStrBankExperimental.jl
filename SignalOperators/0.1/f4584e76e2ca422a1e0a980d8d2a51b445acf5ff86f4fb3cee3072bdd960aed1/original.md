## Arrays

Arrays can be treated as signals. The first dimension is time, the second channels. 

[`AxisArrays`](https://github.com/JuliaArrays/AxisArrays.jl), if they have an axis labeled `time` and one or zero additional axes, can be treated as a signal. The time dimension must be represented using on object with the `step` function defined (e.g. any `AbstractRange`).
