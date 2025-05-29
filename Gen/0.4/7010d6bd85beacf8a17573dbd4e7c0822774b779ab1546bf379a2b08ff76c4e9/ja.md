```
value = get_param_grad(gen_fn::Union{DynamicDSLFunction,StaticIRGenerativeFunction}, name::Symbol)
```

生成関数の学習可能なパラメータの勾配アキュムレータの現在の値を取得します。
