$$
i
$$

-th B-spline基底関数。修正版。

$$
\begin{aligned}
{B}_{(i,p,k)}(t)
&=
\frac{t-k_{i}}{k_{i+p}-k_{i}}{B}_{(i,p-1,k)}(t)
+\frac{k_{i+p+1}-t}{k_{i+p+1}-k_{i+1}}{B}_{(i+1,p-1,k)}(t) \\
{B}_{(i,0,k)}(t)
&=
\begin{cases}
    &1\quad (k_{i} \le t < k_{i+1}) \\
    &1\quad (k_{i} < t = k_{i+1}=k_{l}) \\
    &0\quad (\text{それ以外）
\end{cases}
\end{aligned}
$$

# 例

```jldoctest
julia> P = BSplineSpace{0}(KnotVector(1:6))
BSplineSpace{0, Int64, KnotVector{Int64}}(KnotVector([1, 2, 3, 4, 5, 6]))

julia> bsplinebasis.(P,1:5,(1:6)')
5×6 Matrix{Float64}:
 1.0  0.0  0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0  0.0
 0.0  0.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  1.0  1.0
```
