Staterror doesn't need interpolation, but it's a per-bin modifier. Information regarding which bin is the target is recorded in `bintwoidentity`.

The `δ` is the absolute yield uncertainty in each bin, and the relative uncertainty: `δ` / nominal is taken to be the `σ` of the prior, i.e. `α ~ Normal(1, δ/nominal)`
