```
checkbalance(y; reference="majority")
```

A visual version of `StatsBase.countmap` that returns nothing and prints how      many observations in the dataset belong to each class and their percentage     relative to the size of majority or minority class.

# Arguments

  * `y::AbstractVector`: A vector of categorical values to test for imbalance
  * `reference="majority"`: Either `"majority"` or `"minority"` and decides whether the percentage should be   relative to the size of majority or minority class.

# Example

```julia
num_rows = 50000
num_features = 2
X, y = generate_imbalanced_data(
	num_rows,
	num_features;
	class_probs=[0.8, 0.2],
	type="Matrix",
	rng = 42,
)

julia> Imbalance.checkbalance(y; ref="majority")
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇ 10034 (25.1%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 39966 (100.0%) 

julia> Imbalance.checkbalance(y; ref="minority")
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇ 10034 (100.0%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 39966 (398.3%) 
```
