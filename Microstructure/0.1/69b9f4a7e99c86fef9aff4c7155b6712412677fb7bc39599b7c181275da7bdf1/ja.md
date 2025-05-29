```
train_loop!(
    mlp::Chain, 
    arg::TrainingArg, 
    inputs::Array{Float64,2}, 
    labels::Array{Float64,2}
)
```

`mlp`を訓練し更新し、各エポックの訓練損失、訓練データ損失、および検証データ損失を含む訓練ログのDictを返します。この関数はCPU上で動作し、ほとんどのケースで十分に速いです。
