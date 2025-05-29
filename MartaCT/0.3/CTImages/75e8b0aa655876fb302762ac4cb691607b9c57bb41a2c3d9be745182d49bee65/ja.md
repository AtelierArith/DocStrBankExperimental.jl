```
rescale(x::AbstractArray;
    interval=nothing, calibration=nothing, window=nothing)
```

配列 x を `interval` で指定された区間に再スケーリングします。

`calibration` が `nothing` でない場合、再スケーリングは `calibration` によって与えられた値を参照して行われます。言い換えれば、最小値と最大値は `calibration` によって指定された値であると仮定されます。

参照: [`rescale!`](@ref)
