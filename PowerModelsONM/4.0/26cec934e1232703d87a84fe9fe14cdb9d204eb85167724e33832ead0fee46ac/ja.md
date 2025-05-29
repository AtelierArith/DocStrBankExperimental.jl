```
constraint_isolate_block(pm::AbstractUnbalancedPowerModel, nw::Int)
```

ブロックが隣接するブロックの状態を比較することによって、開いているスイッチによって適切に隔離されることを保証する制約。隣接するブロックのインジケーターが両方とも0または両方とも1でない場合、彼らの間のスイッチはオープン（0）であるべきです。

$$
\begin{align*}
& (z^{bl}_{fr} - z^{bl}_{to}) \leq  \gamma_{i}\ ~\forall i \in S \\
& (z^{bl}_{fr} - z^{bl}_{fr}) \geq - \gamma_{i}\ ~\forall i \in S \\
& z^{bl}_b \leq N_{gen} + N_{strg} + N_{neg load} + \sum_{i \in S \in b} \gamma_i, ~\forall b \in B
\end{align*}
$$

ここで、$z^{bl}_{fr}$ と $z^{bl}_{to}$ はスイッチ $i$ の両側にあるブロックのインジケーター変数です。
