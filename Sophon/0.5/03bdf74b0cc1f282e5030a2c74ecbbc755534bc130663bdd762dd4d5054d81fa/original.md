```
PINNAttention(H_net, U_net, V_net, fusion_layers)
PINNAttention(in_dims::Int, out_dims::Int, activation::Function=sin;
              hidden_dims::Int, num_layers::Int)
```

The output dimesion of `H_net` and the input dimension of `fusion_layers` must be the same. For the second and the third constructor, `Dense` layers is used for `H_net`, `U_net`, and `V_net`. Note that the first constructer does **not** contain the output layer, but the second one does.

```
                 x → U_net → u                           u
                               ↘                           ↘
x → H_net →  h1 → fusionlayer1 → connection → fusionlayer2 → connection
                               ↗                           ↗
                 x → V_net → v                           v
```

## Arguments

  * `H_net`: `AbstractExplicitLayer`.
  * `U_net`: `AbstractExplicitLayer`.
  * `V_net`: `AbstractExplicitLayer`.
  * `fusion_layers`: `Chain`.

## Keyword Arguments

  * `num_layers`: The number of hidden layers.
  * `hidden_dims`: The number of hidden dimensions of each hidden layer.

## Reference

[wang2021understanding](@cite)
