```
reload_neural_model(file)
```

`reload_neural_data` will bring back the parameters from your fit, some details about the optimization (such as the `fit` and bounds vectors) and some details about how you filtered the data. All of the data is not saved in the format that it is loaded by `load_neural_data` because it's too cumbersome to seralize it, so you have to load it again, as above, to re-build `neuralDDM` but you can use some of the stuff that `reload_neural_data` returns to reload the data in the same way (such as `pad` and `dt`)

Returns:

  * `θneural`
  * `neural_options`
  * n
  * cross
  * dt
  * delay
  * pad

See also: [`save_neural_model`](@ref)
