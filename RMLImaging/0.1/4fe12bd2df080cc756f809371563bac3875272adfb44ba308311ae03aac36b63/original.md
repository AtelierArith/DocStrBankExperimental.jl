```
evaluate(domain::AbstractRegularizerDomain, reg::AbstractRegularizer, skymodel::AbstractImageModel, x::AbstractArray)
```

Compute the value of the given regularization function for the given image parameters on the given image model. In default, return 0.

# Arguments

  * `domain::AbstractRegularizerDomain`: the domain of the image where the regularization function will be computed.
  * `reg::AbstractRegularizer`: the regularization function.
  * `skymodel::AbstractImageModel`: the model of the input image
  * `x::AbstractArray`: the parameters of the input image
