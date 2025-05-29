```
in_sample = InSample()
```

Instantiate an `InSample` resampling strategy, for use in `evaluate!`, `evaluate` and in tuning. In this strategy the train and test sets are the same, and consist of all observations specified by the `rows` keyword argument. If `rows` is not specified, all supplied rows are used.

# Example

```julia
using MLJBase, MLJModels

X, y = make_blobs()  # a table and a vector
model = ConstantClassifier()
train, test = partition(eachindex(y), 0.7)  # train:test = 70:30
```

Compute in-sample (training) loss:

```julia
evaluate(model, X, y, resampling=InSample(), rows=train, measure=brier_loss)
```

Compute the out-of-sample loss:

```julia
evaluate(model, X, y, resampling=[(train, test),], measure=brier_loss)
```

Or equivalently:

```julia
evaluate(model, X, y, resampling=Holdout(fraction_train=0.7), measure=brier_loss)
```
