```julia
calculate_factorized_W(sys::AbstractSystem)
```

システムの因子化されたW行列を計算します。

[`Num`](@ref) インスタンスの行列を返します。最初の呼び出しからの結果はシステムオブジェクトにキャッシュされます。
