The `Linearization` structure defines the approximation method of the `Delta` and `Flow` factor nodes.  This method performs a local linearization of f around expansion point x.

!!! note
    The `Linearization` works well for differentiable functions only. The results might not be accurate for non-differentiable functions.


The `Linearization` structure with default parameters can be constructed as `Linearization()`.

The `Linearization` structure is used inside the `DeltaMeta` or `FlowMeta` structures and can be included as:

```
    y ~ f(x) where { meta = DeltaMeta(method = Linearization()) }
    # or
    y ~ Flow(x) where { meta = FlowMeta(flowmodel, Linearization()) }
```
