```
training(
    arg::TrainingArg, 
    net::NetworkArg, 
    rng_seed::Int
)
```

トレーニングを行い、トレーニングされた `mlp` モデル、各エポックのトレインロス、トレーニングデータロス、バリデーションデータロスのトレーニング `logs` の辞書、およびmlpがトレーニングされた `inputs` と `labels`（トレーニングデータ）を返します。この関数は、CPUおよびGPUトレーニングの両方をサポートしています。
