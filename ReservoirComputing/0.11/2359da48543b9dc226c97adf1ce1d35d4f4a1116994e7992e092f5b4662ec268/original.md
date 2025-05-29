```
train(esn::AbstractEchoStateNetwork, target_data, training_method = StandardRidge(0.0))
```

Trains an Echo State Network (ESN) using the provided target data and a specified training method.

# Parameters

  * `esn::AbstractEchoStateNetwork`: The ESN instance to be trained.
  * `target_data`: Supervised training data for the ESN.
  * `training_method`: The method for training the ESN (default: `StandardRidge(0.0)`).

# Example

```jldoctest
julia> train_data = rand(Float32, 10, 100)  # 10 features, 100 time steps
10×100 Matrix{Float32}:
 0.11437   0.425367  0.585867   0.34078   …  0.0531493  0.761425  0.883164
 0.301373  0.497806  0.279603   0.802417     0.49873    0.270156  0.333333
 0.135224  0.660179  0.394233   0.512753     0.901221   0.784377  0.687691
 0.510203  0.877234  0.614245   0.978405     0.332775   0.768826  0.527077
 0.955027  0.398322  0.312156   0.981938     0.473357   0.156704  0.476101
 0.353024  0.997632  0.164328   0.470783  …  0.745613   0.85797   0.465201
 0.966044  0.194299  0.599167   0.040475     0.0996013  0.325959  0.770103
 0.292068  0.495138  0.481299   0.214566     0.819573   0.155951  0.227168
 0.133498  0.451058  0.0761995  0.90421      0.994212   0.332164  0.545112
 0.214467  0.791524  0.124105   0.951805     0.947166   0.954244  0.889733

julia> esn = ESN(train_data, 10, 300; washout=10)
ESN(10 => 300)

julia> output_layer = train(esn, rand(Float32, 3, 90))
OutputLayer successfully trained with output size: 3
```
