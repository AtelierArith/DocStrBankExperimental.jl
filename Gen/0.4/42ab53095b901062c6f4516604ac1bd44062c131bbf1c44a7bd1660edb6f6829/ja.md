```
set_param_grad!(gen_fn::Union{DynamicDSLFunction,StaticIRGenerativeFunction}, name::Symbol, grad_value)
```

生成関数の学習可能なパラメータの勾配累積器を設定します。
