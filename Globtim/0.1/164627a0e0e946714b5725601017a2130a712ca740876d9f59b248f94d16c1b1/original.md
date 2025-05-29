```
init_gaussian_params(n::Int, N::Int, scale::Float64) -> GaussianParams
```

Initialize Gaussian parameters with random centers and variances.

# Arguments

  * `n::Int`: Dimension of the domain.
  * `N::Int`: Number of Gaussian functions.
  * `scale::Float64`: Scaling factor for the variances.

# Returns

  * `GaussianParams`: A struct containing the centers, variances of

the Gaussian functions and a random boolean vector to make a signed sum  of the distributions. 

# Example

```julia params = init*gaussian*params(3, 5, 2.0) println(params.centers)  # Prints the centers of the Gaussian functions println(params.variances)  # Prints the variances of the Gaussian functions
