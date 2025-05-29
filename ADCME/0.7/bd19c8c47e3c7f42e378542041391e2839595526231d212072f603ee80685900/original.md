```
emd(a::Union{PyObject, Array{Float64}}, b::Union{PyObject, Array{Float64}}, M::Union{PyObject, Array{Float64}};
iter::Int64 = 1000, tol::Float64 = 1e-9, returnall::Bool=false)
```

Computes the Earth Mover's Distance, which is defined as 

$$
D(M) = \sum_{i=1}^m \sum_{j=1}^n M_{ij} d_{ij}
$$

Here $M \in \mathbb{R}^{m\times n}$ is the ground distance matrix. The algorithm solves the following optimization problem 

$$
\begin{aligned}\min_{M} &\ D(M)\\\text{s.t.} & \ \sum_{i=1}^m M_{ij} = b_j\\ &\ \sum_{j=1}^n M_{ij} = a_i \end{aligned}
$$

The internal solver for the optimization problem is a netflow solver. The algorithm requires $\sum_i a_i = \sum_j b_j = 1$. 
