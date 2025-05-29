```
BalancedModel(; model=nothing, balancer1=balancer_model1, balancer2=balancer_model2, ...)
BalancedModel(model;  balancer1=balancer_model1, balancer2=balancer_model2, ...)
```

Given a classification model, and one or more balancer models that all implement the `MLJModelInterface`,     `BalancedModel` allows constructing a sequential pipeline that wraps an arbitrary number of balancing models     and a classifier together in a sequential pipeline.

# Operation

  * During training, data is first passed to `balancer1` and the result is passed to `balancer2` and so on, the result from the final balancer   is then passed to the classifier for training.
  * During prediction, the balancers have no effect.

# Arguments

  * `model::Supervised`: A classification model that implements the `MLJModelInterface`.
  * `balancer1::Static=...`: The first balancer model to pass the data to. This keyword argument can have any name.
  * `balancer2::Static=...`: The second balancer model to pass the data to. This keyword argument can have any name.
  * and so on for an arbitrary number of balancers.

# Returns

  * An instance of type ProbabilisticBalancedModel or DeterministicBalancedModel, depending on the prediction type of model.

# Example

```julia
using MLJ
using Imbalance

# generate data
X, y = Imbalance.generate_imbalanced_data(1000, 5; class_probs=[0.2, 0.3, 0.5])

# prepare classification and balancing models
SMOTENC = @load SMOTENC pkg=Imbalance verbosity=0
TomekUndersampler = @load TomekUndersampler pkg=Imbalance verbosity=0
LogisticClassifier = @load LogisticClassifier pkg=MLJLinearModels verbosity=0

oversampler = SMOTENC(k=5, ratios=1.0, rng=42)
undersampler = TomekUndersampler(min_ratios=0.5, rng=42)
logistic_model = LogisticClassifier()

# wrap them in a BalancedModel
balanced_model = BalancedModel(model=logistic_model, balancer1=oversampler, balancer2=undersampler)

# now this behaves as a unified model that can be trained, validated, fine-tuned, etc.
mach = machine(balanced_model, X, y)
fit!(mach)
```
