```
EvaluateEach(geos::AbstractVector{<:AbstractODESolution}, Ts::AbstractVector) -> Vector
```

パラメータのセット `Ts` に対して、ジオデシックのファミリー `geos` を評価します。`geos[1]` は `Ts[1]` で評価され、`geos[2]` は `Ts[2]` で評価される、というように続きます。速度を表す値の後半は自動的に切り捨てられます。
