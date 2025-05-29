```
plot_parameter_distribution(fitted_model, param_priors;
    subplot_titles = Dict(),
    show_distributions = true,
    show_intervals = true,
    prior_color = :green,
    posterior_color = :orange,
    prior_interval_offset = 0,
    posterior_interval_offset = 0.01,
    inner_interval = 0.5,
    outer_interval = 0.8,
    plot_width = 900,
    plot_height = 300)
```

適合したモデルのパラメータの事前分布と事後分布をプロットします。

# 引数

  * 'subplot_titles': パラメータ名とそれに対応するプロットタイトルの辞書。
  * 'show_distributions': 完全な分布を表示するかどうか。
  * 'show_intervals': 不確実性区間を表示するかどうか。
  * 'prior_color': 事前分布の色。
  * 'posterior_color': 事後分布の色。
  * 'prior*interval*offset': 事前区間バーのオフセット。
  * 'posterior*interval*offset': 事後区間バーのオフセット。
  * 'inner_interval': 内部不確実性区間のサイズ。
  * 'outer_interval': 外部不確実性区間のサイズ。
  * 'plot_width': プロットの幅。
  * 'plot_height': プロットの高さ。
