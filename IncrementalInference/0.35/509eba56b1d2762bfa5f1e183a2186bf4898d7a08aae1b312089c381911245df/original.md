```julia
calcProposalBelief(dfg, fct, target; ...)
calcProposalBelief(
    dfg,
    fct,
    target,
    measurement;
    N,
    solveKey,
    nullSurplus,
    dbg
)

```

Compute proposal belief on `vertid` through `fct` representing some constraint in factor graph. Always full dimension variable node – partial constraints will only influence subset of variable dimensions. The remaining dimensions will keep pre-existing variable values.

Notes

  * fulldim is true when "rank-deficient" – TODO swap to false (or even float)
