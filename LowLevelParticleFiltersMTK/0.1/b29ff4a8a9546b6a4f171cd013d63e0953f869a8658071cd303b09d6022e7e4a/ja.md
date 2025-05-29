```
get_filter(prob::StateEstimationProblem, ::Type{ExtendedKalmanFilter}; constant_R1=true, kwargs)
get_filter(prob::StateEstimationProblem, ::Type{UnscentedKalmanFilter}; kwargs)
```

状態推定問題からフィルタをインスタンス化します。`kwargs`はフィルタコンストラクタに送られます。

`constant_R1=true`の場合、動的ノイズ共分散行列`R1`は一定であると仮定され、初期状態で計算されます。そうでない場合、`R1`は外乱入力`w`に対して繰り返し線形化を通じて各時間ステップで計算されます。
