```
constraint_mc_load_power(pm::LPUBFDiagModel, load_id::Int; nw::Int=nw_id_default, report::Bool=true)
```

LPUBFDiagModelのためのデルタ/電圧依存負荷モデル。デルタ負荷は補助電力変数（X）を使用します。定常電流負荷モデルは、フラットスタート電圧解の周りで線形化することによって導出されます。

$$
\begin{align}
&\text{定常電力:} \Rightarrow P_i^d = P_i^{d0},~Q_i^d = Q_i^{d0} ~\forall i \in L \\
&\text{定常インピーダンス（ワイ）:} \Rightarrow P_i^d = a_i \cdot w_i,~Q_i^d = b_i \cdot w_i ~\forall i \in L \\
&\text{定常インピーダンス（デルタ）:} \Rightarrow P_i^d = 3\cdot a_i \cdot w_i,~Q_i^d = 3\cdot b_i \cdot w_i ~\forall i \in L \\
&\text{定常電流（ワイ）:} \Rightarrow P_i^d = \frac{a_i}{2}\cdot \left( 1+w_i \right),~Q_i^d = \frac{b_i}{2}\cdot \left( 1+w_i \right) \forall i \in L \\
&\text{定常電流（デルタ）:} \Rightarrow P_i^d = \frac{\sqrt{3} \cdot a_i}{2}\cdot \left( 1+w_i \right),~Q_i^d = \frac{\sqrt{3} \cdot b_i}{2}\cdot \left( 1+w_i \right) \forall i \in L
\end{align}
$$
