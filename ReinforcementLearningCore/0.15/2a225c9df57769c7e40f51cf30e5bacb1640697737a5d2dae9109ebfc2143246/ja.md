```
(model::CovGaussianNetwork)(rng::AbstractRNG, state::AbstractMatrix; is_sampling::Bool=false, is_return_log_prob::Bool=false)
```

状態の行列を与えると、アクション、μ、およびlogpdfを行列形式で返します。Σのバッチは3Dテンソルのままです。
