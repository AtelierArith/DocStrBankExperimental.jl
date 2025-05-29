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

変数ノード `label::Symbol` を `dfg::AbstractDFG` に追加します。`varType<:InferenceVariable` として。

## 注意事項

  * キーワード `nanosecondtime` は実験的であり、全体のサブセクション部分を意図しています – すなわち accurateTime = (timestamp MOD second) + Nanosecond

## 例

```julia
fg = initfg()
addVariable!(fg, :x0, Pose2)
```
