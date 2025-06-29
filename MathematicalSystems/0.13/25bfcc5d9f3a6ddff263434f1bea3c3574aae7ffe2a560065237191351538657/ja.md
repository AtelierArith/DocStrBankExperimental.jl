```
SecondOrderDiscreteSystem
```

離散時間の二次系の形式：

$$
    Mx_{k+2} + Cx_{k} + f_i(x_k) = f_e(t_k) \forall k.
$$

### フィールド

  * `M`  – 質量行列
  * `C`  – 粘性行列
  * `fi` – 内部力
  * `fe` – 外部力

### ノート

通常、`fi(x_k)` は状態依存関数であり、`fe` は与えられたベクトルです。この実装では、それぞれの型 `FI` と `FE` は汎用的です。
