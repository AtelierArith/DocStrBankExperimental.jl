```
mjd_transitionFD(m, d, eps, flg_centered, A, B, C, D)
```

有限差分遷移行列（制御理論の表記）   d(x_next) = A*dx + B*du   d(sensor) = C*dx + D*du   必要な出力行列の次元:      A: (2*nv+na x 2*nv+na)      B: (2*nv+na x nu)      D: (nsensordata x 2*nv+na)      C: (nsensordata x nu)

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`eps::Float64`**
  * **`flg_centered::UInt8`**
  * **`A::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`A`は形状(2*nv+na, 2*nv+na)である必要があります。必要ない場合は`nothing`に設定できます。
  * **`B::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`B`は形状(2*nv+na, nu)である必要があります。必要ない場合は`nothing`に設定できます。
  * **`C::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`C`は形状(nsensordata, 2*nv+na)である必要があります。必要ない場合は`nothing`に設定できます。
  * **`D::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`D`は形状(nsensordata, nu)である必要があります。必要ない場合は`nothing`に設定できます。
