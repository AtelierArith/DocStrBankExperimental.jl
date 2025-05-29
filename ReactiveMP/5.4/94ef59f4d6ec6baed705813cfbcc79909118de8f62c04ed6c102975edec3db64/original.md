The `Unscented` structure defines the approximation method of the `Delta` and `Flow` factor nodes.  More specifically, it contains the hyperparameters used for sigma points computation.

# Arguments

  * `α`: Spread parameter for unscented transform #1
  * `β`: Algorithm parameter for incorporating prior information on the (non-Gaussian) distribution of Delta node input
  * `κ`: Spread parameter for unscented transform #2
  * `e`: Internal cache

The `Unscented` structure with default parameters can be constructed as `Unscented()`.

The `Unscented` structure is used inside the `DeltaMeta` or `FlowMeta` structure and can be included as: 

```
    y ~ f(x) where { meta = DeltaMeta(method = Unscented()) }
    # or
    y ~ Flow(x) where { meta = FlowMeta(flowmodel, Unscented()) }
```
