```
ForwardDiff.derivative(f!, y::AbstractArray, x::Real, cfg::DerivativeConfig = DerivativeConfig(f!, y, x), check=Val{true}())
```

`df!/dx` を `x` で評価します。`f!` は `f!(y, x)` として呼び出され、結果は `y` に格納されます。

`check` を `Val{false}()` に設定すると、タグチェックが無効になります。これは摂動の混乱を引き起こす可能性があるため、注意して使用する必要があります。
