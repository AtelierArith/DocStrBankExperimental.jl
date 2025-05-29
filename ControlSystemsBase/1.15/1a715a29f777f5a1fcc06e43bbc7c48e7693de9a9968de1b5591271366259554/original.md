```
add_input(sys::AbstractStateSpace, B2::AbstractArray, D2 = 0)
```

Add inputs to `sys` by forming

$$
\begin{aligned}
x' &= Ax + [B \; B_2]u \\
y  &= Cx + [D \; D_2]u \\
\end{aligned}
$$

If `B2` is an integer it will be interpreted as an index and an input matrix containing a single 1 at the specified index will be used.

Example: The following example forms an innovation model that takes innovations as inputs

```julia
G   = ssrand(2,2,3, Ts=1)
K   = kalman(G, I(G.nx), I(G.ny))
sys = add_input(G, K)
```
