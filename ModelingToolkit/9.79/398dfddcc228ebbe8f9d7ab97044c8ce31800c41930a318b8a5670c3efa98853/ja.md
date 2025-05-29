```julia
calculate_hessian(sys::AbstractSystem)
```

スカラーシステムのヘッセ行列を計算します。

[`Num`](@ref) インスタンスの行列を返します。最初の呼び出しからの結果はシステムオブジェクトにキャッシュされます。
