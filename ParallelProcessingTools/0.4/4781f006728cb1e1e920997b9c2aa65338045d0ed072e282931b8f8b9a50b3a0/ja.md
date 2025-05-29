```
abstract type AbstractThreadLocal{T} end
```

型 `T` のスレッドローカル値のための抽象型です。

現在のスレッドの値は `getindex(::AbstractThreadLocal)` および `setindex(::AbstractThreadLocal, x)` を介してアクセスされます。

通常の値とスレッドローカル値の両方に統一的にアクセスするには、関数 [`getlocalvalue`](@ref) を使用してください。

すべてのスレッドにわたるすべての値を取得するには、関数 [`getallvalues`](@ref) を使用してください。

デフォルトの実装は [`ThreadLocal`](@ref) です。
