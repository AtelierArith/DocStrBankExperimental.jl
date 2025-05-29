```julia
create_NLS_problem_using_ForwardDiff(r::Function;domain_image_dim::Pair{Int,Int})
```

Creates an [`AbstractNLS`](@ref) specialized instance where the [`eval_r_J`](@ref) function is automatically defined using automatic differentiation.

  * `r` is a function that maps a parameter vector θ to its residue. The Jacobian matrix is computed using the `ForwardDiff` package.
  * `domain_image_dim` is a pair of the form `θ length => r length` that defines domain and codomain dimensions.

# Usage example

An example defining the Rosenbrock function

$$
\frac{1}{2}\|r(\theta)\|^2\text{ where }r = \sqrt{2} \left( \begin{array}{c}  1-\theta_1 \\ 10(\theta_2-\theta_1^2) \end{array} \right)
$$

```julia
nls = create_NLS_problem_using_ForwardDiff(2 => 2) do θ
     sqrt(2) sqrt(2)* [ 1-θ[1], 10*(θ[2]-θ[1]^2) ]* [ 1-θ[1], 10*(θ[2]-θ[1]^2) ]
end
```
