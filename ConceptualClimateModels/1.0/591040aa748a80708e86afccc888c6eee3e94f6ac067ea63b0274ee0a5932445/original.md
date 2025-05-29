```
SigmoidProcess <: Process
SigmoidProcess(variable, driver; left, right, scale, reference)
```

A common process for when a `variable` has a sigmoidal dependence on a `driver` variable. The rest of the input arguments should be real numbers or `@parameter` named parameters.

The process creates a sigmoidal relationship based on the `tanh` function:

```
variable ~ left + (right - left)*(1 + tanh(2(driver - reference)/scale))*0.5
```

i.e., the variable goes from value `left` to value `right` as `driver` increases over a range of `scale` (centered at `reference`). Instead of `reference` you may provide `start` or `finish` keywords, which make `reference = start + scale/2` or `reference = finish - scale/2` respectively.

If the values given to the parameters of the expression are real numbers, they become named parameters prefixed with the name of `variable`, then the name of the `driver`, and then `_sigmoid_left`, `_sigmoid_right`, `_sigmoid_rate` and `_sigmoid_ref` respectively. Use `LiteralParameter` for parameters you do not wish to rename.
