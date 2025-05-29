TreeParzen.MLJTreeParzen

MLJTuning.jlのためのTreeParzen.jlインターフェースオーバーライドを含むサブモジュール

オブジェクト:

  * `MLJTreeParzenSpace`
  * `MLJTreeParzenTuning`

`MLJTreeParzenTuning`オブジェクトのためにオーバーライドされたMLJTuningメソッド:

  * `default_n`
  * `result`
  * `models!`
  * `setup`

使用例:

```julia
# ] add MLJBase MLJModels MLJTuning DecisionTree

using MLJBase, MLJModels, MLJTuning, TreeParzen
X, y = @load_iris

@load DecisionTreeClassifier

space = (Dict(
    :min_purity_increase => HP.Uniform(:min_purity_increase, 0.0, 1.0),
    :merge_purity_threshold => HP.Uniform(:merge_purity_threshold, 0.0, 1.0),
    :pdf_smoothing => HP.Uniform(:pdf_smoothing, 0.0, 1.0),
))

dtc = DecisionTreeClassifier()

tm = TunedModel(
    model=dtc,
    ranges=space,
    tuning=MLJTreeParzen.MLJTreeParzenTuning(),
    n=250,
    resampling=CV(nfolds=3),
    measure=cross_entropy
)

mach = machine(tm, X, y)
fit!(mach)

best_model = fitted_params(mach).best_model
@show(best_model.min_purity_increase)
@show(best_model.merge_purity_threshold)
@show(best_model.pdf_smoothing)
```
