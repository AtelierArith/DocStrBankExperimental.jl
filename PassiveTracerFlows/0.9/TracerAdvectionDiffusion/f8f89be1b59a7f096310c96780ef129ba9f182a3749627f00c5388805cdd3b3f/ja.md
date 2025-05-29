```
Problem(dev::Device=CPU(), MQGprob::FourierFlows.Problem; parameters...)
```

デバイス `dev` 上で定常拡散問題を構築し、`GeophysicalFlows.MultiLayerQG` 問題からの流れを移流流れとして使用します。デフォルトのデバイスとして `CPU()` が設定されています。
