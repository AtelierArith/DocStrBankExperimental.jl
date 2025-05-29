```julia
fft!(
    out::AbstractArray{T, 1},
    in::AbstractArray{U, 1},
    start_out::Int64,
    start_in::Int64,
    d::FFTA.Direction,
    _::FFTA.CompositeFFT,
    g::FFTA.CallGraph{T},
    idx::Int64
)

```

Cooley-Tukey composite FFT, with a pre-computed call graph

# Arguments

`out`: Output vector `in`: Input vector `start_out`: Index of the first element of the output vector `start_in`: Index of the first element of the input vector `d`: Direction of the transform `g`: Call graph for this transform `idx`: Index of the current transform in the call graph
