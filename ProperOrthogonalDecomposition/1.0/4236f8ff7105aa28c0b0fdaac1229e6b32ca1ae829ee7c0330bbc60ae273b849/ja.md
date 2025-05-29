```
function modeConvergence(X::AbstractArray, PODfun, stops::AbstractArray{<: AbstractRange}, numModes::Int)
```

モード収束チェックは、モードのl2ノルムに基づいています。配列 `stops` には、`stops[end]` が参照モードとして使用される範囲が含まれています。計算時間を短縮するために、`numModes` の最大のモードが比較されます。データをPODするために使用される関数は、`PODfun` を通じて提供されます。
