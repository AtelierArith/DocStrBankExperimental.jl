```
SecondOrderConstrainedLinearControlDiscreteSystem
```

離散時間の二次制約線形制御システムの形式：

$$
    Mx_{k+2} + Cx_{k+1} + Kx_k = Bu_k, \; x_k ∈ \mathcal{X}, \; u_k ∈ \mathcal{U} \; \forall k.
$$

### フィールド

  * `M` – 質量行列
  * `C` – 粘性行列
  * `K` – 剛性行列
  * `B` – 入力行列
  * `X` – 状態制約
  * `U` – 入力制約
