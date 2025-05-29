```
Stack(; metalearner=nothing, name1=model1, name2=model2, ..., keyword_options...)
```

Implements the two-layer generalized stack algorithm introduced by [Wolpert (1992)](https://www.sciencedirect.com/science/article/abs/pii/S0893608005800231) and generalized by [Van der Laan et al (2007)](https://biostats.bepress.com/ucbbiostat/paper222/). Returns an instance of type `ProbabilisticStack` or `DeterministicStack`, depending on the prediction type of `metalearner`.

When training a machine bound to such an instance:

  * The data is split into training/validation sets according to the specified `resampling` strategy.
  * Each base model `model1`, `model2`, ... is trained on each training subset and outputs predictions on the corresponding validation sets. The multi-fold predictions are spliced together into a so-called out-of-sample prediction for each model.
  * The adjudicating model, `metalearner`, is subsequently trained on the out-of-sample predictions to learn the best combination of base model predictions.
  * Each base model is retrained on all supplied data for purposes of passing on new production data onto the adjudicator for making new predictions

### Arguments

  * `metalearner::Supervised`: The model that will optimize the desired criterion based on its internals.  For instance, a LinearRegression model will optimize the squared error.
  * `resampling`: The resampling strategy used to prepare out-of-sample predictions of the base learners.
  * `measures`: A measure or iterable over measures, to perform an internal evaluation of the learners in the Stack while training. This is not for the evaluation of the Stack itself.
  * `cache`: Whether machines created in the learning network will cache data or not.
  * `acceleration`: A supported `AbstractResource` to define the training parallelization mode of the stack.
  * `name1=model1, name2=model2, ...`: the `Supervised` model instances to be used as base learners.  The provided names become properties of the instance created to allow hyper-parameter access

### Example

The following code defines a `DeterministicStack` instance for learning a `Continuous` target, and demonstrates that:

  * Base models can be `Probabilistic` models even if the stack itself is `Deterministic` (`predict_mean` is applied in such cases).
  * As an alternative to hyperparameter optimization, one can stack multiple copies of given model, mutating the hyper-parameter used in each copy.

```julia
using MLJ

DecisionTreeRegressor = @load DecisionTreeRegressor pkg=DecisionTree
EvoTreeRegressor = @load EvoTreeRegressor
XGBoostRegressor = @load XGBoostRegressor
KNNRegressor = @load KNNRegressor pkg=NearestNeighborModels
LinearRegressor = @load LinearRegressor pkg=MLJLinearModels

X, y = make_regression(500, 5)

stack = Stack(;metalearner=LinearRegressor(),
                resampling=CV(),
                measures=rmse,
                constant=ConstantRegressor(),
                tree_2=DecisionTreeRegressor(max_depth=2),
                tree_3=DecisionTreeRegressor(max_depth=3),
                evo=EvoTreeRegressor(),
                knn=KNNRegressor(),
                xgb=XGBoostRegressor())

mach = machine(stack, X, y)
evaluate!(mach; resampling=Holdout(), measure=rmse)

```

The internal evaluation report can be accessed like this and provides a PerformanceEvaluation object for each model:

```julia
report(mach).cv_report
```
