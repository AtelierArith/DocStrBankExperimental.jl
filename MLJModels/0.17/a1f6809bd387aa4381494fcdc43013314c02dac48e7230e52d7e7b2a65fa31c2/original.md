```
BinaryThresholdPredictor(model; threshold=0.5)
```

Wrap the `Probabilistic` model, `model`, assumed to support binary classification, as a `Deterministic` model, by applying the specified `threshold` to the positive class probability. In addition to conventional supervised classifiers, it can also be applied to outlier detection models that predict normalized scores - in the form of appropriate `UnivariateFinite` distributions - that is, models that subtype `AbstractProbabilisticUnsupervisedDetector` or `AbstractProbabilisticSupervisedDetector`.

By convention the positive class is the second class returned by `levels(y)`, where `y` is the target.

If `threshold=0.5` then calling `predict` on the wrapped model is equivalent to calling `predict_mode` on the atomic model.

# Example

Below is an application to the well-known Pima Indian diabetes dataset, including optimization of the `threshold` parameter, with a high balanced accuracy the objective. The target class distribution is 500 positives to 268 negatives.

Loading the data:

```julia
using MLJ, Random
rng = Xoshiro(123)

diabetes = OpenML.load(43582)
outcome, X = unpack(diabetes, ==(:Outcome), rng=rng);
y = coerce(Int.(outcome), OrderedFactor);
```

Choosing a probabilistic classifier:

```julia
EvoTreesClassifier = @load EvoTreesClassifier
prob_predictor = EvoTreesClassifier()
```

Wrapping in `TunedModel` to get a deterministic classifier with `threshold` as a new hyperparameter:

```julia
point_predictor = BinaryThresholdPredictor(prob_predictor, threshold=0.6)
Xnew, _ = make_moons(3, rng=rng)
mach = machine(point_predictor, X, y) |> fit!
predict(mach, X)[1:3] # [0, 0, 0]
```

Estimating performance:

```julia
balanced = BalancedAccuracy(adjusted=true)
e = evaluate!(mach, resampling=CV(nfolds=6), measures=[balanced, accuracy])
e.measurement[1] # 0.405 ± 0.089
```

Wrapping in tuning strategy to learn `threshold` that maximizes balanced accuracy:

```julia
r = range(point_predictor, :threshold, lower=0.1, upper=0.9)
tuned_point_predictor = TunedModel(
    point_predictor,
    tuning=RandomSearch(rng=rng),
    resampling=CV(nfolds=6),
    range = r,
    measure=balanced,
    n=30,
)
mach2 = machine(tuned_point_predictor, X, y) |> fit!
optimized_point_predictor = report(mach2).best_model
optimized_point_predictor.threshold # 0.260
predict(mach2, X)[1:3] # [1, 1, 0]
```

Estimating the performance of the auto-thresholding model (nested resampling here):

```julia
e = evaluate!(mach2, resampling=CV(nfolds=6), measure=[balanced, accuracy])
e.measurement[1] # 0.477 ± 0.110
```
