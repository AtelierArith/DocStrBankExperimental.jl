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

高次元の信念の周辺分布とさまざまなキーワードオプションを許可する一般的なKDEプロット関数です。

## `Position2`の例:

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

## `Pose2`の例:

```julia
# TODO
```
