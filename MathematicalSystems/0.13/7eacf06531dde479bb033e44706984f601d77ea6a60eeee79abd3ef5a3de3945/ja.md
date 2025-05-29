```
SecondOrderConstrainedContinuousSystem
```

連続時間制約付き二次系の形式：

$$
    Mx''(t) + Cx'(t) + f_i(x) = f_e(t) \forall t, x ∈ X, f_e(t) ∈ U
$$

### フィールド

  * `M`  – 質量行列
  * `C`  – 粘性行列
  * `fi` – 内部力
  * `fe` – 外部力
  * `X`  – 状態集合
  * `U`  – 入力集合
