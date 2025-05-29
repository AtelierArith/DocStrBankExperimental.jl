```
TransformedTargetModel(model; transformer=nothing, inverse=nothing, cache=true)
```

Wrap the supervised or semi-supervised `model` in a transformation of the target variable.

Here `transformer` one of the following:

  * The `Unsupervised` model that is to transform the training target. By default (`inverse=nothing`) the parameters learned by this transformer are also used to inverse-transform the predictions of `model`, which means `transformer` must implement the `inverse_transform` method. If this is not the case, specify `inverse=identity` to suppress inversion.
  * A callable object for transforming the target, such as `y -> log.(y)`. In this case a callable `inverse`, such as `z -> exp.(z)`, should be specified.

Specify `cache=false` to prioritize memory over speed, or to guarantee data anonymity.

Specify `inverse=identity` if `model` is a probabilistic predictor, as inverse-transforming sample spaces is not supported. Alternatively, replace `model` with a deterministic model, such as `Pipeline(model, y -> mode.(y))`.

### Examples

A model that normalizes the target before applying ridge regression, with predictions returned on the original scale:

```julia
@load RidgeRegressor pkg=MLJLinearModels
model = RidgeRegressor()
tmodel = TransformedTargetModel(model, transformer=Standardizer())
```

A model that applies a static `log` transformation to the data, again returning predictions to the original scale:

```julia
tmodel2 = TransformedTargetModel(model, transformer=y->log.(y), inverse=z->exp.(y))
```
