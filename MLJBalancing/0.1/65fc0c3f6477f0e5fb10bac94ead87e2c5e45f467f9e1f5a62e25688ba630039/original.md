```
BalancedBaggingClassifier
```

A model type for constructing a balanced bagging classifier, based on [MLJBalancing.jl](https://github.com/JuliaAI/MLJBalancing).

From MLJ, the type can be imported using

`BalancedBaggingClassifier = @load BalancedBaggingClassifier pkg=MLJBalancing`

Construct an instance with default hyper-parameters using the syntax `bagging_model = BalancedBaggingClassifier(model=...)`

Given a probablistic classifier.`BalancedBaggingClassifier` performs bagging by undersampling only majority data in each bag so that its includes as much samples as in the minority data. This is proposed with an Adaboost classifier where the output scores are averaged in the paper Xu-Ying Liu, Jianxin Wu, & Zhi-Hua Zhou. (2009). Exploratory Undersampling for Class-Imbalance Learning. IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics), 39 (2), 539–5501

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

where

  * `X`: input features of a form supported by the `model` being wrapped (typically a table, e.g., `DataFrame`,   with `Continuous` columns will be supported, as a minimum)
  * `y`: the binary target, which can be any `AbstractVector` where `length(unique(y)) == 2`

Train the machine with `fit!(mach, rows=...)`.

# Hyperparameters

  * `model::Probabilistic`: The classifier to use to train on each bag.
  * `T::Integer=0`: The number of bags to be used in the ensemble. If not given, will be set as   the ratio between the frequency of the majority and minority classes. Can be later found in `report(mach)`.
  * `rng::Union{AbstractRNG, Integer}=default_rng()`: Either an `AbstractRNG` object or an `Integer`    seed to be used with `Xoshiro` if Julia `VERSION>=1.7`. Otherwise, uses MersenneTwister`.

# Operations

  * `predict(mach, Xnew)`: return predictions of the target given

features `Xnew` having the same scitype as `X` above. Predictions are probabilistic, but uncalibrated.

  * `predict_mode(mach, Xnew)`: return the mode of each prediction above

# Example

```julia
using MLJ
using Imbalance

# Load base classifier and BalancedBaggingClassifier
BalancedBaggingClassifier = @load BalancedBaggingClassifier pkg=MLJBalancing
LogisticClassifier = @load LogisticClassifier pkg=MLJLinearModels verbosity=0

# Construct the base classifier and use it to construct a BalancedBaggingClassifier
logistic_model = LogisticClassifier()
model = BalancedBaggingClassifier(model=logistic_model, T=5)

# Load the data and train the BalancedBaggingClassifier
X, y = Imbalance.generate_imbalanced_data(100, 5; num_vals_per_category = [3, 2],
                                            class_probs = [0.9, 0.1],
                                            type = "ColTable",
                                            rng=42)
julia> Imbalance.checkbalance(y)
1: ▇▇▇▇▇▇▇▇▇▇ 16 (19.0%)
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 84 (100.0%)

mach = machine(model, X, y) |> fit!

# Predict using the trained model

yhat = predict(mach, X)     # probabilistic predictions
predict_mode(mach, X)       # point predictions
```
