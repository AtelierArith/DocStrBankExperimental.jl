```
plot_activation(activation = [:relu,:σ,:swish,:tanh];
                plot_deriv::Bool  = false,
                show_plot::Bool   = true,
                save_plot::Bool   = false,
                plot_png::String  = "act_func.png")
```

Plot activation function(s) or their derivative(s).

**Arguments:**

  * `activation`: activation function(s) to plot

      * `relu`  = rectified linear unit
      * `σ`     = sigmoid (logistic function)
      * `swish` = self-gated
      * `tanh`  = hyperbolic tan
  * `plot_deriv`: (optional) if true, plot activation function(s) derivative(s)
  * `show_plot`:  (optional) if true, show `p1`
  * `save_plot`:  (optional) if true, save `p1` as `plot_png`
  * `plot_png`:   (optional) plot file name to save (`.png` extension optional)

**Returns:**

  * `p1`: plot of activation function(s) or their derivative(s)
