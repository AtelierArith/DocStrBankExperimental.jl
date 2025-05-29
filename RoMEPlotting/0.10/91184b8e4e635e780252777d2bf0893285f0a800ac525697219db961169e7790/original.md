```julia
plotBelief(
    fgl,
    sym;
    solveKey,
    dims,
    title,
    levels,
    fill,
    layers,
    c,
    overlay
)

```

A peneric KDE plotting function that allows marginals of higher dimensional beliefs and various keyword options.

## Example for `Position2`:

```julia

p = manikde!(Position2, [randn(2) for _ in 1:100])
q = manikde!(Position2, [randn(2).+[5;0] for _ in 1:100])

plotBelief(p)
plotBelief(p, dims=[1;2], levels=3)
plotBelief(p, dims=[1])

plotBelief([p;q])
plotBelief([p;q], dims=[1;2], levels=3)
plotBelief([p;q], dims=[1])
```

## Example for `Pose2`:

```julia
# TODO
```
