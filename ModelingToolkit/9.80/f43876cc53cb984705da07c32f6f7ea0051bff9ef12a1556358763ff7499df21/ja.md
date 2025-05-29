```julia
calculate_jacobian(sys::AbstractSystem)
```

システムのヤコビ行列を計算します。

[`Num`](@ref) インスタンスの行列を返します。最初の呼び出しからの結果はシステムオブジェクトにキャッシュされます。
