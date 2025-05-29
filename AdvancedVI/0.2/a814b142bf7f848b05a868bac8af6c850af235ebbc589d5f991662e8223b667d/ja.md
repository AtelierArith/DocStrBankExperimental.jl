```
vi(model, alg::VariationalInference)
vi(model, alg::VariationalInference, q::VariationalPosterior)
vi(model, alg::VariationalInference, getq::Function, θ::AbstractArray)
```

`model`から変分事後分布を構築し、与えられた`VariationalInference`インスタンスの設定に従って最適化を実行します。

# 引数

  * `model`: `Turing.Model`または`Function` z ↦ log p(x, z) で、ここで`x`は観測を示します
  * `alg`: 使用されるVIアルゴリズム
  * `q`: 変分目的の専門的な実装が存在することが想定される`VariationalPosterior`
  * `getq`: パラメータ`θ`を入力として受け取り、`VariationalPosterior`を返す関数
  * `θ`: `getq`が使用される場合のみ必要で、その場合は変分事後分布の初期パラメータです
