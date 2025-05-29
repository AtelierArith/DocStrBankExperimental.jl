```
InvertFlow(fo::FlowOp)
```

Creates a flow operator that is the invert of `fo`.

# Example

```julia
inv_tanh_flow = InvertFlow(TanhFlow(2))
```
