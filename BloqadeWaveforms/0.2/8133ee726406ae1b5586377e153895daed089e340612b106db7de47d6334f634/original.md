```
smooth([kernel=Kernel.gaussian], f; edge_pad_size::Int=length(f.clocks))
```

Kernel smoother function for piece-wise linear function/waveform via weighted moving average method.

# Arguments

  * `kernel`: the kernel function, default is [`Kernels.gaussian`](@ref).
  * `f`: a [`Union{PiecewiseLinear, PiecewiseConstant}`](@ref) function or a [`Waveform{<:Union{PiecewiseLinear, PiecewiseConstant}}`](@ref).

# Keyword Arguments

  * `kernel_radius`: radius of the kernel.
  * `edge_pad_size`: the size of edge padding.
