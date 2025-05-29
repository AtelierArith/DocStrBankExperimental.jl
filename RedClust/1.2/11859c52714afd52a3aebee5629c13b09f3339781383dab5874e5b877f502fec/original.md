```
example_dataset(n::Int)
```

Returns a named tuple containing the dataset from the n$^{\mathrm{th}}$ simulated example in the main paper. This dataset was generated using the following code in Julia v1.8.1:

```julia
	using RedClust
	using Random: seed!
	seed!(44)
	K = 10 # Number of clusters
	N = 100 # Number of points
	data_σ = [0.25, 0.2, 0.18][n] # Variance of the normal kernel
	data_dim = [10, 50, 10][n] # Data dimension
	data = generatemixture(N, K; α = 10, σ = data_σ, dim = data_dim);
```

Note however that the above code may produce different results on your computer because the random number generator in Julia is not meant for reproducible results across different computers, different versions of Julia, or different versions of the Random.jl package, even with appropriate seeding. Therefore the datasets have been included with this package, and it is recommended to access them via this function.

See also [`generatemixture`](@ref).
