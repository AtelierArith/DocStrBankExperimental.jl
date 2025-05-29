```
fit_vi(model; n_samples=4000, n_iterations=10, n_elbo_samples=20, 
       optimizer=AutoForwardDiff())
```

ADVI（自動微分変分推論）を使用して変分推論を実行します。

# 引数

  * `model`: 推論を行うモデルインスタンス
  * `n_samples::Int=4000`: 引く事後サンプルの数
  * `n_iterations::Int=10`: ADVIの反復回数
  * `n_elbo_samples::Int=20`: ELBO推定のためのサンプル数
  * `optimizer=AutoForwardDiff()`: ADVIのための最適化アルゴリズム

# 戻り値

  * `ADVIResults`: 推論結果を含むコンテナで、以下を含みます：

      * 事後サンプル
      * MAP推定
      * パラメータの分散
      * 完全なTuringチェーン

# 注意事項

Turing.jlのADVI実装を使用して、高速な近似ベイズ推論を行います。モデルは適切な事前分布と尤度で自動的に構築されます。
