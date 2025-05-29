```
ae_init(output_dims::Array{Int64}; T::Type=Float64, method::String="xavier")
fc_init(output_dims::Array{Int64})
```

Return the initial weights and bias values by TensorFlow as a vector. The neural network architecture is

$$
o_1 (\text{Input layer}) \rightarrow o_2 \rightarrow \ldots \rightarrow o_n (\text{Output layer})
$$

Three types of  random initializers are provided

  * `xavier` (default). It is useful for `tanh` fully connected neural network.

```
W^l_i \sim \mathcal{N}\left(0, \sqrt{\frac{1}{n_{l-1}}}\right)
```

  * `xavier_avg`. A variant of `xavier`

$$
W^l_i \sim \mathcal{N}\left(0, \sqrt{\frac{2}{n_l + n_{l-1}}}\right)
$$

  * `he`. This is the activation aware initialization of weights and helps mitigate the problem

of vanishing/exploding gradients. 

$$
W^l_i \sim \mathcal{N}\left(0, \sqrt{\frac{2}{n_{l-1}}}\right)
$$

# Example

```julia
x = constant(rand(10,30))
θ = fc_init([30, 20, 20, 5])
y = fc(x, [20, 20, 5], θ) # 10×5
```
