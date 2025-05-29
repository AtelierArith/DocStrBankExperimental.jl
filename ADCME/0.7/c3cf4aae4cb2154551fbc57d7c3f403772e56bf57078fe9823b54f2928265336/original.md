```
sinkhorn(a::Union{PyObject, Array{Float64}}, b::Union{PyObject, Array{Float64}}, M::Union{PyObject, Array{Float64}};
reg::Float64 = 1.0, iter::Int64 = 1000, tol::Float64 = 1e-9, method::String="sinkhorn")
```

Computes the optimal transport with Sinkhorn algorithm. The mathematical formulation is 

$$
\begin{aligned}
\arg\min_P &\ \left(P, M\right) + \lambda \Omega(\Gamma)\\ 
\text{s.t.} &\ \Gamma 1 = a\\ 
&\ \Gamma^T 1 = b\\ 
& \Gamma \geq 0 
\end{aligned}
$$

Here $\Omega$ is the entropic regularization. Note if $\lambda$ is very small, the algorithm may encounter numerical instabilities. 

The implementation are adapted from https://github.com/rflamary/POT.  
