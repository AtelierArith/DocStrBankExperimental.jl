```
RecursiveFeatureElimination(model; n_features=0, step=1)
```

This model implements a recursive feature elimination algorithm for feature selection. It recursively removes features, training a base model on the remaining features and evaluating their importance until the desired number of features is selected.

# Training data

In MLJ or MLJBase, bind an instance `rfe_model` to data with

```
mach = machine(rfe_model, X, y)
```

OR, if the base model supports weights, as

```
mach = machine(rfe_model, X, y, w)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of the scitype as that required by the base model; check column scitypes with `schema(X)` and column scitypes required by base model with `input_scitype(basemodel)`.
  * `y` is the target, which can be any table of responses whose element scitype is   `Continuous` or `Finite` depending on the `target_scitype` required by the base model;   check the scitype with `scitype(y)`.
  * `w` is the observation weights which can either be `nothing`(default) or an `AbstractVector` whoose element scitype is `Count` or `Continuous`. This is different from `weights` kernel which is an hyperparameter to the model, see below.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * model: A base model with a `fit` method that provides information on feature feature importance (i.e `reports_feature_importances(model) == true`)
  * n_features::Real = 0: The number of features to select. If `0`, half of the features are selected. If a positive integer, the parameter is the absolute number of features to select. If a real number between 0 and 1, it is the fraction of features to select.
  * step::Real=1: If the value of step is at least 1, it signifies the quantity of features to eliminate in each iteration. Conversely, if step falls strictly within the range of 0.0 to 1.0, it denotes the proportion (rounded down) of features to remove during each iteration.

# Operations

  * `transform(mach, X)`: transform the input table `X` into a new table containing only columns corresponding to features accepted by the RFE algorithm.
  * `predict(mach, X)`: transform the input table `X` into a new table same as in `transform(mach, X)` above and predict using the fitted base model on the transformed table.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `features_left`: names of features remaining after recursive feature elimination.
  * `model_fitresult`: fitted parameters of the base model.

# Report

The fields of `report(mach)` are:

  * `scores`: dictionary of scores for each feature in the training dataset. The model deems highly scored variables more significant.
  * `model_report`: report for the fitted base model.

# Examples

The following example assumes you have MLJDecisionTreeInterface in the active package ennvironment.

```
using MLJ

RandomForestRegressor = @load RandomForestRegressor pkg=DecisionTree

# Creates a dataset where the target only depends on the first 5 columns of the input table.
A = rand(50, 10);
y = 10 .* sin.(
        pi .* A[:, 1] .* A[:, 2]
    ) + 20 .* (A[:, 3] .- 0.5).^ 2 .+ 10 .* A[:, 4] .+ 5 * A[:, 5];
X = MLJ.table(A);

# fit a rfe model:
rf = RandomForestRegressor()
selector = RecursiveFeatureElimination(rf, n_features=2)
mach = machine(selector, X, y)
fit!(mach)

# view the feature importances
feature_importances(mach)

# predict using the base model trained on the reduced feature set:
Xnew = MLJ.table(rand(50, 10));
predict(mach, Xnew)

# transform data with all features to the reduced feature set:
transform(mach, Xnew)
```
