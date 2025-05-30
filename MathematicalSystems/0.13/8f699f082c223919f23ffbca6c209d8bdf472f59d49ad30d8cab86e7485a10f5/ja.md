```
SecondOrderConstrainedLinearControlContinuousSystem
```

連続時間の二次制約付き線形制御システムの形式：

$$
    Mx''(t) + Cx'(t) + Kx(t) = Bu(t), \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U} \; \forall t.
$$

### フィールド

  * `M` – 質量行列
  * `C` – 粘性行列
  * `K` – 剛性行列
  * `B` – 入力行列
  * `X` – 状態制約
  * `U` – 入力制約
