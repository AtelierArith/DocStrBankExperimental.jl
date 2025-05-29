```
set_param!(gen_fn::Union{DynamicDSLFunction,StaticIRGenerativeFunction}, name::Symbol, value)
```

生成関数の学習可能なパラメータの値を設定します。

注意: 勾配累積器の値は更新されません。
