```
impulse!(out::AbstractArray, arma::ARMAProcess, ε0::Real=1.0)
```

`ε0`で指定されたインパルスに対する`arma`プロセスの応答を計算し、結果を`out`に格納します。計算されるホライズンの数は`out`の長さによって決まります。詳細は[`impulse`](@ref)および[`simulate!`](@ref)を参照してください。
