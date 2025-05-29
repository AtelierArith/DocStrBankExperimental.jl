```
get_nn_m(Nf::Int, Ny::Int = 1;
         hidden                = [8],
         activation::Function  = swish,
         final_bias::Bool      = true,
         skip_con::Bool        = false,
         model_type::Symbol    = :m1
         l_window::Int         = 5,
         tf_layer_type::Symbol = :postlayer,
         tf_norm_type::Symbol  = :batch,
         dropout_prob::Real    = 0.2,
         N_tf_head::Int        = 8,
         tf_gain::Real         = 1.0)
```

Get neural network model. Valid for 0-3 hidden layers, except for `model_type = :m3w, :m3tf`, which are only valid for 1 or 2 hidden layers.

**Arguments:**

  * `Nf`:            length of input (feature) layer
  * `Ny`:            (optional) length of output layer
  * `hidden`:        (optional) hidden layers & nodes (e.g., `[8,8]` for 2 hidden layers, 8 nodes each)
  * `activation`:    (optional) activation function

      * `relu`  = rectified linear unit
      * `σ`     = sigmoid (logistic function)
      * `swish` = self-gated
      * `tanh`  = hyperbolic tan
      * run `plot_activation()` for a visual
  * `final_bias`:    (optional) if true, include final layer bias
  * `skip_con`:      (optional) if true, use skip connections, must have length(`hidden`) == 1
  * `model_type`:    (optional) aeromagnetic compensation model type
  * `l_window`:      (optional) temporal window length, only used for `model_type = :m3w, :m3tf`
  * `tf_layer_type`: (optional) transformer normalization layer before or after skip connection {`:prelayer`,`:postlayer`}, only used for `model_type = :m3tf`
  * `tf_norm_type`:  (optional) normalization for transformer encoder {`:batch`,`:layer`,`:none`}, only used for `model_type = :m3tf`
  * `dropout_prob`:  (optional) dropout rate, only used for `model_type = :m3w, :m3tf`
  * `N_tf_head`:     (optional) number of attention heads, only used for `model_type = :m3tf`
  * `tf_gain`:       (optional) weight initialization parameter, only used for `model_type = :m3tf`

**Returns:**

  * `m`: neural network model
