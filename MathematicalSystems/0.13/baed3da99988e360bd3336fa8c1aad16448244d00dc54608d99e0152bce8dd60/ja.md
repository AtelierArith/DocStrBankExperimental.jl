```
制約付きアフィン制御離散システム
```

連続時間アフィン制御システムで、次の形式のドメイン制約があります：

$$
    x_{k+1} = A x_k + B u_k + c, \; x_k ∈ \mathcal{X}, \; u_k ∈ \mathcal{U} \; \forall k.
$$

### フィールド

  * `A` – 状態行列
  * `B` – 入力行列
  * `c` – アフィン項
  * `X` – 状態制約
  * `U` – 入力制約
