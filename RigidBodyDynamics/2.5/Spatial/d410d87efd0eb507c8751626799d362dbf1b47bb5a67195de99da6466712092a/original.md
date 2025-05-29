```julia
struct Twist{T}
```

A twist represents the relative angular and linear motion between two bodies.

The twist of frame $j$ with respect to frame $i$, expressed in frame $k$ is defined as

$$
T_{j}^{k,i}=\left(\begin{array}{c}
\omega_{j}^{k,i}\\
v_{j}^{k,i}
\end{array}\right)\in\mathbb{R}^{6}
$$

such that

$$
\left[\begin{array}{cc}
\hat{\omega}_{j}^{k,i} & v_{j}^{k,i}\\
0 & 0
\end{array}\right]=H_{i}^{k}\dot{H}_{j}^{i}H_{k}^{j}
$$

where $H^{\beta}_{\alpha}$ is the homogeneous transform from frame $\alpha$ to frame $\beta$, and $\hat{x}$ is the $3 \times 3$ skew symmetric matrix that satisfies $\hat{x} y = x \times y$ for all $y \in \mathbb{R}^3$.

Here, $\omega_{j}^{k,i}$ is the angular part and $v_{j}^{k,i}$ is the linear part. Note that the linear part is not in general the same as the linear velocity of the origin of frame $j$.
