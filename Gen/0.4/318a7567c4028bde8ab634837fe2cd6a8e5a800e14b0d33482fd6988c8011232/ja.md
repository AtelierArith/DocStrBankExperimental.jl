```
init_param!(gen_fn::Union{DynamicDSLFunction,StaticIRGenerativeFunction}, name::Symbol, value)
```

生成関数の名前付きトレーニング可能パラメータの値を初期化します。

また、そのパラメータの勾配累積器を `zero(value)` に生成します。

例:

```julia
init_param!(foo, :theta, 0.6)
```
