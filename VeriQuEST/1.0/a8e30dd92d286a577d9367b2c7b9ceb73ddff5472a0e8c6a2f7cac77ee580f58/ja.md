```
add_noise!(model::Union{Damping,Dephasing,Depolarising,Pauli}, params::QubitNoiseParameters)
```

与えられたノイズパラメータに基づいて量子モデルにノイズを追加します。

# 引数

  * `model::Union{Damping,Dephasing,Depolarising,Pauli}`: ノイズを追加する量子モデル。
  * `params::QubitNoiseParameters`: ノイズの種類と強さを指定するノイズパラメータ。
