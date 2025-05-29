```
jumpk(x; k=6)
```

**JumpK**関数は、最大値の直前にサイズ$k$の谷を持つ[`onemax`](@ref)関数の修正です。ヒルクライマーが最大値に到達する唯一の方法は、$k$ビットの*完全な反転*であり、これは非常に困難と見なされます。

$$
\text{JUMP}_k(x) = \begin{cases}
\lVert{x}\rVert_1 & \quad \text{if } \lVert x \rVert_1 \in [0..n-k] \cup \{n\},\\
-\lVert x \rVert_1 & \quad \text{otherwise}
\end{cases}
$$

ここで、$\lVert x \rVert_1 = \sum_{i=1}^n x_i$は、$x \in \{0, 1\}^n$の1ビットの数です。
