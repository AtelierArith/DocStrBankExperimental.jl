```
MoreauEnvelope(f, γ=1)
```

Return the Moreau envelope (also known as Moreau-Yosida regularization) of function `f` with parameter `γ` (positive), that is

$$
f^γ(x) = \min_z \left\{ f(z) + \tfrac{1}{2γ}\|z-x\|^2 \right\}.
$$

If $f$ is convex, then $f^γ$ is a smooth, convex, lower approximation to $f$, having the same minima as the original function.
