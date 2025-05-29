```julia
Config(
;
    threshold,
    linear_forgetting,
    draws,
    random_trials,
    prior_weight
) -> TreeParzen.Configuration.Config

```

キーワード引数外部コンストラクタ

  * `threshold::Float64`; デフォルト 0.25.
  * `linear_forgetting::Int`; デフォルト 25.`
  * `draws::Int`; デフォルト 24. `
  * `random_trials::Int`; デフォルト 20.
  * `prior_weight::Float64`; デフォルト 1.0.
