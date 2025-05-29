```
function modeConvergence!(loadFun, PODfun, stops::AbstractArray{<: AbstractRange}, numModes::Int)
```

`modeConvergence(X::AbstractArray, PODfun, stops::AbstractArray{<: AbstractRange}, numModes::Int)` と同様ですが、ここでは各比較のためにデータが再ロードされるため、最大メモリ使用量を削減するためにインプレースPODメソッドを使用できます。
