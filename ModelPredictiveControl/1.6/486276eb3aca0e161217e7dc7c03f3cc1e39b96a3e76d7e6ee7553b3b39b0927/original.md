```
LinModel(sys::TransferFunction[, Ts]; i_u=1:size(sys,2), i_d=Int[])
```

Convert to minimal realization state-space when `sys` is a transfer function.

`sys` is equal to $\frac{\mathbf{y}(s)}{\mathbf{z}(s)}$ for continuous-time, and  $\frac{\mathbf{y}(z)}{\mathbf{z}(z)}$, for discrete-time.

See also [`tf`](@extref ControlSystemsBase.tf)

# Examples

```jldoctest
julia> model = LinModel([tf(3, [30, 1]) tf(-2, [5, 1])], 0.5, i_d=[2])
LinModel with a sample time Ts = 0.5 s and:
 1 manipulated inputs u
 2 states x
 1 outputs y
 1 measured disturbances d
```
