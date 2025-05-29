```
DeepONet(branch_net, trunk_net;
         flatten_layer=FlattenLayer(),
         linear_layer=NoOpLayer(),
         bias=ScalarLayer())
DeepONet(layer_sizes_branch, activation_branch,
         layer_sizes_trunk,
         activation_trunk,
         layer_sizes_linear=nothing)
```

Deep operator network. Note that the branch net supports multi-dimensional inputs. The `flatten_layer` flatten the output of the branch net to a matrix, and the `linear_layer` is applied to the flattened. In this case, `linear_layer` must be given to transform the flattened matrix to the correct shape.

```
v → branch_net → flatten_layer → linear_layer → b
                                                  ↘
                                                    b' * t + bias → u
                                                  ↗
                                ξ → trunk_net → t
```

## Arguments

  * `branch_net`: The branch net.
  * `trunk_net`: The trunk net.

## Keyword Arguments

  * `flatten_layer`: The layer to flatten a multi-dimensional array to a matrix.
  * `linear_layer`: The layer to apply a linear transformation to the output of the `flatten_layer`.

## Inputs

  * `(v, ξ)`: `v` is an array of shape $(b_1,b_2,...b_d, m)$, which is a discretization of $m$ functions from $R^d$ to $R$. $ξ$ is a matrix of shape $(d', n)$, representing $n$ data points of the domain $R^{d'}$.

## Returns

  * A matrix of shape $(m, n)$.

## Examples

```julia
julia> deeponet = DeepONet((3, 5, 4), relu, (2, 6, 4, 4), tanh)
DeepONet(
    branch_net = Chain(
        layer_1 = Dense(3 => 5, relu),  # 20 parameters
        layer_2 = Dense(5 => 4),        # 24 parameters
    ),
    trunk_net = Chain(
        layer_1 = Dense(2 => 6, tanh_fast),  # 18 parameters
        layer_2 = Dense(6 => 4, tanh_fast),  # 28 parameters
        layer_3 = Dense(4 => 4, tanh_fast),  # 20 parameters
    ),
    flatten_layer = FlattenLayer(),
    linear_layer = NoOpLayer(),
    bias = ScalarLayer(),                    # 1 parameters
)         # Total: 111 parameters,
          #        plus 0 states, summarysize 80 bytes.
```

## Reference

[lu2019deeponet](@cite)
