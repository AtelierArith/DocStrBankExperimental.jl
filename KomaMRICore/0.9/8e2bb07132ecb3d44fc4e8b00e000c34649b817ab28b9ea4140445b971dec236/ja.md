```
mag = simulate_slice_profile(seq; z, sim_params)
```

シーケンス構造体を実行した後の `z` に沿ったスピンの磁化を返します。

# 引数

  * `seq`: (`::Sequence`) シーケンス構造体

# キーワード

  * `z`: (`=range(-2e-2,2e-2,200)`) z軸の範囲
  * `sim_params`: (`::Dict{String, Any}`, `=Dict{String,Any}("Δt_rf"=>1e-6)`) シミュレーションパラメータを含む辞書

# 返り値

  * `mag`: (`::SpinStateRepresentation`) 磁化ベクトルの最終状態
