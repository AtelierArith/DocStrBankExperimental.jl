```
hrep(halfspaces::HalfSpaceIt; d::FullDim)
```

全次元 `d` の多面体の H-表現を、半空間 `halfspaces` の交差として作成します。

### 例

例えば、多面体

$$
\begin{aligned}
  x_1 + x_2 &\leq 1 \\
  x_1 - x_2 &\leq 0 \\
  x_1 & \geq 0.
\end{aligned}
$$

は次のように作成できます：

```julia
hrep([HalfSpace([1, 1], 1), HalfSpace([1, -1], 0), HalfSpace([-1, 0], 0)])
```
