```
diffusion_map(P, d; t=1)
diffusion_map(X, kernel, d; t=1)
```

compute diffusion map. 

two call signatures:

  * the data matrix `X` is passed in. examples are in the columns.
  * the right-stochastic matrix `P` is passed in. (eg. for a precomputed kernel matrix)

# arguments

  * `d`: dim
  * `t`: # of steps

# example

```julia
# define kernel
kernel(xᵢ, xⱼ) = gaussian_kernel(xᵢ, xⱼ, 0.5)

# data matrix (100 data pts, 2D vectors)
X = rand(2, 100)

# diffusion map to 1D
X̂ = diff_map(X, kernel, 1)
```
