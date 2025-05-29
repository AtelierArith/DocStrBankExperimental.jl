```julia
calculate_control_jacobian(sys::AbstractSystem)
```

システムの制御に関するヤコビ行列を計算します。

[`Num`](@ref) インスタンスの行列を返します。最初の呼び出しからの結果はシステムオブジェクトにキャッシュされます。
