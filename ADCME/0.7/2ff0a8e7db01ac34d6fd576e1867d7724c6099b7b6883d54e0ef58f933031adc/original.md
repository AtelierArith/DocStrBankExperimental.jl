```
nnuq(H::Array{Float64,2}, invR::Union{Float64, Array{Float64,2}}, invQ::Union{Float64, Array{Float64,2}})
```

Returns the variance matrix for the Baysian inversion. 

The negative log likelihood function is

$$
l(s) =\frac{1}{2} (y-h(s))^T R^{-1} (y-h(s)) + \frac{1}{2} s^T Q^{-1} s
$$

The covariance matrix is computed by first linearizing $h(s)$

$$
h(s)\approx h(s_0) + \nabla h(s_0) (s-s_0)
$$

and then computing the second order derivative

$$
V = \left(\frac{\partial^2 l}{\partial s^T\partial s}\right)^{-1} = (H^T R^{-1} H + Q^{-1})^{-1}
$$

Note the result is independent of $s_0$, $y_0$, and only depends on $\nabla h(s_0)$
