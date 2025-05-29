```
get_noise_model_params(model::Union{Damping,Dephasing,Depolarising,Pauli}, server_qureg::Union{DensityMatrix,Qureg})
```

指定されたノイズモデルとサーバー量子レジスタのノイズモデルパラメータを取得します。

# 引数

  * `model::Union{Damping,Dephasing,Depolarising,Pauli}`: パラメータを取得するノイズモデル。
  * `server_qureg::Union{DensityMatrix,Qureg}`: サーバー量子レジスタ。

# 戻り値

  * 指定されたノイズモデルとサーバー量子レジスタのノイズパラメータ。

```
