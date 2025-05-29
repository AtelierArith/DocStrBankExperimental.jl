```
SecondOrderConstrainedDiscreteSystem
```

離散時間制約二次系の形式：

$$
    Mx_{k+2} + Cx_{k} + f_i(x_k) = f_e(t_k) \forall k, x_k ∈ X, f_e(t_k) ∈ U
$$

### フィールド

  * `M`  – 質量行列
  * `C`  – 粘性行列
  * `fi` – 内部力
  * `fe` – 外部力
  * `X`  – 状態集合
  * `U`  – 入力集合
