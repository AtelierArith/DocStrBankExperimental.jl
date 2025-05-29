```
IndependentMOKernel(k::Kernel)
```

Kernel for multiple independent outputs with kernel `k` each.

# Definition

For inputs $x, x'$ and output dimensions $p, p'$, the kernel $\widetilde{k}$ for independent outputs with kernel $k$ each is defined as

$$
\widetilde{k}\big((x, p), (x', p')\big) = \begin{cases}
    k(x, x') & \text{if } p = p', \\
    0 & \text{otherwise}.
\end{cases}
$$

Mathematically, it is equivalent to a matrix-valued kernel defined as

$$
\widetilde{K}(x, x') = \mathrm{diag}\big(k(x, x'), \ldots, k(x, x')\big) \in \mathbb{R}^{m \times m},
$$

where $m$ is the number of outputs.
