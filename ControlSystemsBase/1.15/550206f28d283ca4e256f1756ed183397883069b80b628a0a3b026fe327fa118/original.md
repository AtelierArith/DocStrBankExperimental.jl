```
add_output(sys::AbstractStateSpace, C2::AbstractArray, D2 = 0)
```

Add outputs to `sys` by forming

$$
\begin{aligned}
x' &= Ax + Bu \\
y  &= [C; C_2]x + [D; D_2]u \\
\end{aligned}
$$

If `C2` is an integer it will be interpreted as an index and an output matrix containing a single 1 at the specified index will be used.

When called with `C2 = I(sys.nx)`, this function is in some settings known to as `augstate`.
