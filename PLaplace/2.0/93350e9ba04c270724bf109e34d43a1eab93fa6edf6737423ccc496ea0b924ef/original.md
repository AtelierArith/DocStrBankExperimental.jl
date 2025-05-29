```julia
xpnorm(
    p::Float64,
    dv::AbstractDict{Tuple{Int64, Int64}, AbstractVector{Float64}},
    w::AbstractVector{Float64}
) -> Float64

```

Returns $\Vert f \Vert^p_{X_p(\Omega)} = \int_{\Omega} \Vert ∇ f(x) \Vert_2^p \;\mathrm{d}x$ in FEM representaion, i.e.

$$
\Vert f \Vert^p_{X_p(T_{h_\Omega})} =
    \sum\limits_{i=1}^m \omega_i 
    \left(\sum\limits_{j=1}^d \sum\limits_{r=1}^{d^\prime}
    [D^{(j,r)} v]_i^2 \right)^{\frac{p}{2}}.
$$

Parameters can either be given as a function and a mesh or with the function as FEM coefficient vector and a derivative tensor.

# Mandatory Arguments

  * `p::Float64`: Parameter for the norm.
  * `dv::AbstractDict{Tuple{Int64,Int64},AbstractVector{Float64}}`: Discrete derivative of   function v given at the quadrature nodes of the elements in $T_{h_\Omega}$.
  * `w::AbstractVector{Float64}`: Vector of weights corresponding to the quadrature nodes.
