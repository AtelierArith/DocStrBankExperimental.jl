```
get_param_dict_advi()
```

ADVI（自動微分変分推論）アルゴリズムのデフォルトパラメータ辞書を取得します。

# 戻り値

ADVIパラメータのデフォルト値を含む辞書：

  * `n_samples`: 引くポスタリオサンプルの数（デフォルト：4000）
  * `n_iterations`: ADVIの反復回数（デフォルト：50）
  * `n_elbo_samples`: ELBO推定のためのサンプル数（デフォルト：20）
  * `autodiff`: 自動微分バックエンド（デフォルト：AutoForwardDiff()）
