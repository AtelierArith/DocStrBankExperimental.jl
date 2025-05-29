```
mj_constraintUpdate(m, d, jar, cost, flg_coneHessian)
```

efc*state、efc*force、qfrc_constraint、および（オプションで）コーンヘッセ行列を計算します。costがNULLでない場合、*cost = s(jar)を設定します。ここで、jar = Jac*qacc-arefです。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`jar::Vector{Float64}`** -> 可変サイズのベクトル。`jar`はベクトルである必要があり、行列ではありません。`jar`のサイズはnefcと等しい必要があります。定数。
  * **`cost::Vector{Float64}`** -> サイズ1の**オプション**ベクトル。`cost`はサイズ1のベクトルである必要があります。必要ない場合は`nothing`に設定できます。
  * **`flg_coneHessian::Int32`**
