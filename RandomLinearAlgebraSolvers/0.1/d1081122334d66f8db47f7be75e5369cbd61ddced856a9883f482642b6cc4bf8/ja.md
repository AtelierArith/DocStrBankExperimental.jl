```
stp = RLAStopping(A, b::S; n_listofstates::Int = 0, kwargs...)
```

このパッケージに特化した`LAStopping`の作成者。問題である`stp.pb`は、`A`が密であれば`Stopping.LinearSystem`であり、そうでなければ`LLSModels.LLSModel`です。状態は、長さ`|b|`の残差`stp.current_state.res`のためのスペースを確保します。この停止は、最適性を宣言するために`stp.current_state.res`の無限ノルムを使用します。
