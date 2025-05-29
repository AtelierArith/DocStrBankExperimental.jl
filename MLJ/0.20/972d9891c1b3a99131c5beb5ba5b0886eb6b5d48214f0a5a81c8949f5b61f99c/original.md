MLJ

[`MLJ`](https://juliaai.github.io/MLJ.jl//dev/) is a Machine Learning toolbox for Julia. It collects together functionality from separate components listed below, which can be loaded individually.

Actual model code (e.g., code for instantiating a `DecisionTreeClassifier`) must be explicitly loaded from the model-providing package, using `@load`, for example. However core model wrappers and some common transformers are immediately available; do `localmodels(wrappers=true)` at startup to list.

# Components

  * MLJBase.jl: The `machine` interface, tools to `partition` and `unpack` datasets, `evaluate`/`evaluate!` for model performance, `|>` pipeline syntax, `TransformedTargetModel` wrapper, general model composition syntax (learning networks), synthetic data generators, `scitype` and `schema` methods (from ScientificTypes.jl) for checking how MLJ interprets your data. Generally required for any MLJ workflow.
  * StatisticalMeasures.jl: MLJ-compatible measures (metrics) for machine learning, confusion matrices, ROC curves.
  * MLJModels.jl: Common transformers for data preprocessing, searching the model registry, loading models with `@load`
  * MLJTuning.jl: Hyperparameter optimization via `TunedModel` wrapper
  * MLJIteration.jl: `IteratedModel` Wrapper for controlling iterative models
  * MLJEnsembles.jl: Homogeneous model ensembling, via the `EnsembleModel` wrapper
  * MLJBalancing.jl: Incorporation of oversampling/undersampling methods in pipelines, via the `BalancedModel` wrapper
  * FeatureSelection.jl: Transformers for feature selection, and the supervised model wrapper `RecursiveFeatureSelection`.
  * MLJFlow.jl: Integration with MLflow workflow tracking
  * OpenML.jl: Tool for grabbing datasets from OpenML.org
