```julia
calculate_tgrad(sys::AbstractTimeDependentSystem)
```

システムの時間勾配を計算します。

[`Num`](@ref) インスタンスのベクトルを返します。最初の呼び出しからの結果はシステムオブジェクトにキャッシュされます。
