```
TunableQPSafetyFilter(cbfs::Vector{ControlBarrierFunction}, Σ::ControlAffineSystem, kd::Function; tunable=false)
```

cbfと希望するコントローラからTunableQPSafetyFilterを構築します。

# キーワード引数

  * `tunable::Bool` : 拡張クラスK関数の係数を決定変数にするかどうかを決定するブール値
