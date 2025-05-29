```julia
addVariable!(
    dfg,
    label,
    varTypeU;
    N,
    solvable,
    timestamp,
    nanosecondtime,
    dontmargin,
    tags,
    smalldata,
    checkduplicates,
    initsolvekeys
)

```

Add a variable node `label::Symbol` to `dfg::AbstractDFG`, as `varType<:InferenceVariable`.

## Notes

  * keyword `nanosecondtime` is experimental and intended as the whole subsection portion – i.e. accurateTime = (timestamp MOD second) + Nanosecond

## Example

```julia
fg = initfg()
addVariable!(fg, :x0, Pose2)
```
