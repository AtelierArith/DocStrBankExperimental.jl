```
Pipeline(component1, component2, ... , componentk; options...)
Pipeline(name1=component1, name2=component2, ..., namek=componentk; options...)
component1 |> component2 |> ... |> componentk
```

Create an instance of a composite model type which sequentially composes the specified components in order. This means `component1` receives inputs, whose output is passed to `component2`, and so forth. A "component" is either a `Model` instance, a model type (converted immediately to its default instance) or any callable object. Here the "output" of a model is what `predict` returns if it is `Supervised`, or what `transform` returns if it is `Unsupervised`.

Names for the component fields are automatically generated unless explicitly specified, as in

```julia
Pipeline(encoder=ContinuousEncoder(drop_last=false),
         stand=Standardizer())
```

The `Pipeline` constructor accepts keyword `options` discussed further below.

Ordinary functions (and other callables) may be inserted in the pipeline as shown in the following example:

```
Pipeline(X->coerce(X, :age=>Continuous), OneHotEncoder, ConstantClassifier)
```

### Syntactic sugar

The `|>` operator is overloaded to construct pipelines out of models, callables, and existing pipelines:

```julia
LinearRegressor = @load LinearRegressor pkg=MLJLinearModels add=true
PCA = @load PCA pkg=MultivariateStats add=true

pipe1 = MLJBase.table |> ContinuousEncoder |> Standardizer
pipe2 = PCA |> LinearRegressor
pipe1 |> pipe2
```

At most one of the components may be a supervised model, but this model can appear in any position. A pipeline with a `Supervised` component is itself `Supervised` and implements the `predict` operation.  It is otherwise `Unsupervised` (possibly `Static`) and implements `transform`.

### Special operations

If all the `components` are invertible unsupervised models (ie, implement `inverse_transform`) then `inverse_transform` is implemented for the pipeline. If there are no supervised models, then `predict` is nevertheless implemented, assuming the last component is a model that implements it (some clustering models). Similarly, calling `transform` on a supervised pipeline calls `transform` on the supervised component.

### Transformers that need a target in training

Some transformers that have type `Unsupervised` (so that the output of `transform` is propagated in pipelines) may require a target variable for training. An example are so-called target encoders (which transform categorical input features, based on some target observations). Provided they appear before any `Supervised` component in the pipelines, such models are supported. Of course a target must be provided whenever training such a pipeline, whether or not it contains a `Supervised` component.

### Optional key-word arguments

  * `prediction_type`  - prediction type of the pipeline; possible values: `:deterministic`, `:probabilistic`, `:interval` (default=`:deterministic` if not inferable)
  * `operation` - operation applied to the supervised component model, when present; possible values: `predict`, `predict_mean`, `predict_median`, `predict_mode` (default=`predict`)
  * `cache` - whether the internal machines created for component models should cache model-specific representations of data (see [`machine`](@ref)) (default=`true`)

!!! warning
    Set `cache=false` to guarantee data anonymization.


To build more complicated non-branching pipelines, refer to the MLJ manual sections on composing models.
